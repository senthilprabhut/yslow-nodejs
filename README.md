yslow-nodejs
=====

YSlow analyzes web pages and suggests ways to improve their performance based on a set of [rules for high performance web pages](http://developer.yahoo.com/performance/rules.html

yslow-nodejs is forked from yslow's (https://github.com/marcelduran/yslow) nodejs component and fixed jsdom version to 3.1.2 and upgraded yslow to version 3.1.8

# Installation

    npm install yslow-nodejs -g

# Help

    yslow-nodejs --help

```
Usage: yslow-nodejs [options] [file ...]

  Options:

    -h, --help               output usage information
    -V, --version            output the version number
    -i, --info <info>        specify the information to display/log (basic|grade|stats|comps|all) [basic]
    -f, --format <format>    specify the output results format (json|xml|plain) [json]
    -r, --ruleset <ruleset>  specify the YSlow performance ruleset to be used (ydefault|yslow1|yblog) [ydefault]
    -b, --beacon <url>       specify an URL to log the results
    -d, --dict               include dictionary of results fields
    -v, --verbose            output beacon response information

  Examples:

    yslow-nodejs file.har
    yslow-nodejs -i grade -f xml -b http://server.com/beacon file1.har file2.har
    yslow-nodejs --info all --format plain /tmp/*.har
    yslow-nodejs -i basic --rulseset yslow1 -d < file.har
    curl example.com/file.har | yslow -i grade -b http://server.com/beacon -v

  More Info:

     https://yslow.org/user-guide/#version2
```

# As a module

    node

```js
> require('fs').readFile('example.com.har', function (err, data) {
    var har = JSON.parse(data),
        YSLOW = require('yslow-nodejs').YSLOW,
        doc = require('jsdom').jsdom(),
        res = YSLOW.harImporter.run(doc, har, 'ydefault'),
        content = YSLOW.util.getResults(res.context, 'basic');

    console.log(content);
});
{ w: 98725, o: 89, u: 'http%3A%2F%2Fexample.com%2F', r: 9, i: 'ydefault', lt: 981 }
```

More Info
---------

[yslow.org](http://yslow.org)

Licensing
---------

Copyright (c) 2012, Yahoo! Inc. All rights reserved.  
Copyright (c) 2013, Marcel Duran and other contributors. All rights reserved.  
Copyrights licensed under the New BSD License. See the accompanying LICENSE file for terms.
