# api documentation for  [git-tools (v0.2.1)](https://github.com/scottgonzalez/node-git-tools)  [![npm package](https://img.shields.io/npm/v/npmdoc-git-tools.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-git-tools) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-git-tools.svg)](https://travis-ci.org/npmdoc/node-npmdoc-git-tools)
#### Tools for parsing data out of git repositories.

[![NPM](https://nodei.co/npm/git-tools.png?downloads=true)](https://www.npmjs.com/package/git-tools)

[![apidoc](https://npmdoc.github.io/node-npmdoc-git-tools/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-git-tools_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-git-tools/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-git-tools/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-git-tools/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Scott González",
        "email": "scott.gonzalez@gmail.com",
        "url": "http://scottgonzalez.com"
    },
    "bugs": {
        "url": "https://github.com/scottgonzalez/node-git-tools/issues"
    },
    "dependencies": {
        "spawnback": "~1.0.0"
    },
    "description": "Tools for parsing data out of git repositories.",
    "devDependencies": {
        "grunt": "~0.4.0",
        "grunt-contrib-jshint": "~0.1.1",
        "grunt-contrib-nodeunit": "~0.1.2",
        "rimraf": "~2.1.4"
    },
    "directories": {},
    "dist": {
        "shasum": "6e1846af2c0e91ab59258b48f9b53c1279b3b273",
        "tarball": "https://registry.npmjs.org/git-tools/-/git-tools-0.2.1.tgz"
    },
    "gitHead": "d2d1bf4f908231da84ea5e6cb23ca4c76e3bc779",
    "homepage": "https://github.com/scottgonzalez/node-git-tools",
    "keywords": [
        "git"
    ],
    "main": "git-tools.js",
    "maintainers": [
        {
            "name": "scott.gonzalez",
            "email": "scott.gonzalez@gmail.com"
        }
    ],
    "name": "git-tools",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/scottgonzalez/node-git-tools.git"
    },
    "scripts": {},
    "version": "0.2.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module git-tools](#apidoc.module.git-tools)
1.  [function <span class="apidocSignatureSpan">git-tools.</span>clone ( options, callback )](#apidoc.element.git-tools.clone)
1.  [function <span class="apidocSignatureSpan">git-tools.</span>isRepo ( path, callback )](#apidoc.element.git-tools.isRepo)
1.  [function <span class="apidocSignatureSpan">git-tools.</span>parsePerson ( person )](#apidoc.element.git-tools.parsePerson)



# <a name="apidoc.module.git-tools"></a>[module git-tools](#apidoc.module.git-tools)

#### <a name="apidoc.element.git-tools.clone"></a>[function <span class="apidocSignatureSpan">git-tools.</span>clone ( options, callback )](#apidoc.element.git-tools.clone)
- description and source-code
```javascript
clone = function ( options, callback ) {
	var dir = options.dir;
	var args = [ "clone", options.repo, dir ];
	options = copy( options );
	delete options.repo;
	delete options.dir;

	Object.keys( options ).forEach(function( option ) {
		args.push( "--" + option );

		var value = options[ option ];
		if ( value !== true ) {
			args.push( value );
		}
	});

	args.push(function( error ) {
		if ( error ) {
			return callback( error );
		}

		callback( null, new Repo( dir ) );
	});

	var repo = new Repo( process.cwd() );
	repo.exec.apply( repo, args );
}
```
- example usage
```shell
...
});
'''



## API

### Repo.clone( options, callback )

Clones a repository and returns the new 'Repo' instance.

* 'options' (Object): Options for cloning the repository.
* 'repo' (String): The repository to clone from.
* 'path' (String): The path to clone into.
* extra: Additional options can be provided, as documented below.
...
```

#### <a name="apidoc.element.git-tools.isRepo"></a>[function <span class="apidocSignatureSpan">git-tools.</span>isRepo ( path, callback )](#apidoc.element.git-tools.isRepo)
- description and source-code
```javascript
isRepo = function ( path, callback ) {
	var repo = new Repo( path );
	repo.isRepo( callback );
}
```
- example usage
```shell
...
	dir: "/tmp/git-tools",
	depth: 5
});
'''



### Repo.isRepo( path, callback )

Determines if the specified path is a git repository.

* 'path' (String): The path to check.
* 'callback' (Function; 'function( error, isRepo )'): Function to invoke after determining if the path is a git repository.
* 'isRepo' (Boolean): Whether the path is a git repository.
...
```

#### <a name="apidoc.element.git-tools.parsePerson"></a>[function <span class="apidocSignatureSpan">git-tools.</span>parsePerson ( person )](#apidoc.element.git-tools.parsePerson)
- description and source-code
```javascript
parsePerson = function ( person ) {
		var matches = rPerson.exec( person );
		return {
			email: matches[ 1 ],
			name: matches[ 2 ]
		};
	}
```
- example usage
```shell
...

			authorMap[ author ]++;
			totalCommits++;
		});

		authors = Object.keys( authorMap ).map(function( author ) {
			var commits = authorMap[ author ];
			return extend( Repo.parsePerson( author ), {
				commits: commits,
				commitsPercent: (commits * 100 / totalCommits).toFixed( 1 )
			});
		}).sort(function( a, b ) {
			return b.commits - a.commits;
		});
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
