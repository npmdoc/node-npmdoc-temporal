# api documentation for  [temporal (v0.5.0)](https://github.com/rwaldron/temporal)  [![npm package](https://img.shields.io/npm/v/npmdoc-temporal.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-temporal) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-temporal.svg)](https://travis-ci.org/npmdoc/node-npmdoc-temporal)
#### Non-blocking, temporal task sequencing and scheduling.

[![NPM](https://nodei.co/npm/temporal.png?downloads=true)](https://www.npmjs.com/package/temporal)

[![apidoc](https://npmdoc.github.io/node-npmdoc-temporal/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-temporal_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-temporal/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-temporal/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-temporal/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Rick Waldron",
        "email": "waldron.rick@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/rwaldron/temporal/issues"
    },
    "contributors": [
        {
            "name": "Matthieu Dehaussy",
            "email": "<mdehaussy@carlipa.com"
        },
        {
            "name": "Taha Hesham",
            "email": "<taha@wizylabs.com"
        }
    ],
    "dependencies": {
        "es6-shim": "latest"
    },
    "description": "Non-blocking, temporal task sequencing and scheduling.",
    "devDependencies": {
        "grunt": "0.4.1",
        "grunt-contrib-jshint": "latest",
        "grunt-contrib-nodeunit": "latest",
        "grunt-contrib-watch": "latest",
        "grunt-jsbeautifier": "latest"
    },
    "directories": {},
    "dist": {
        "shasum": "5b818954c8dabcd2f8b22610782342328b82414c",
        "tarball": "https://registry.npmjs.org/temporal/-/temporal-0.5.0.tgz"
    },
    "engines": {
        "node": ">=0.10.0"
    },
    "gitHead": "3ef38a682933c044cb7bf003d8158822293fc818",
    "homepage": "https://github.com/rwaldron/temporal",
    "keywords": [
        "schedule",
        "task",
        "settimeout",
        "setinterval",
        "nexttick",
        "process",
        "sequence",
        "sequencing",
        "loop",
        "repeat",
        "wait",
        "delay",
        "sleep"
    ],
    "licenses": [
        {
            "type": "MIT",
            "url": "https://github.com/rwaldron/temporal/blob/master/LICENSE-MIT"
        }
    ],
    "main": "lib/temporal",
    "maintainers": [
        {
            "name": "rwaldron",
            "email": "waldron.rick@gmail.com"
        }
    ],
    "name": "temporal",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/rwaldron/temporal.git"
    },
    "scripts": {
        "test": "grunt"
    },
    "version": "0.5.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module temporal](#apidoc.module.temporal)
1.  [function <span class="apidocSignatureSpan">temporal.</span>clear ()](#apidoc.element.temporal.clear)
1.  [function <span class="apidocSignatureSpan">temporal.</span>defer (time, operation)](#apidoc.element.temporal.defer)
1.  [function <span class="apidocSignatureSpan">temporal.</span>delay (time, operation)](#apidoc.element.temporal.delay)
1.  [function <span class="apidocSignatureSpan">temporal.</span>loop (time, operation)](#apidoc.element.temporal.loop)
1.  [function <span class="apidocSignatureSpan">temporal.</span>queue (tasks)](#apidoc.element.temporal.queue)
1.  [function <span class="apidocSignatureSpan">temporal.</span>repeat (n, ms, callback)](#apidoc.element.temporal.repeat)
1.  [function <span class="apidocSignatureSpan">temporal.</span>wait (time, operation)](#apidoc.element.temporal.wait)
1.  number <span class="apidocSignatureSpan">temporal.</span>_eventsCount
1.  object <span class="apidocSignatureSpan">temporal.</span>_events
1.  object <span class="apidocSignatureSpan">temporal.</span>domain



# <a name="apidoc.module.temporal"></a>[module temporal](#apidoc.module.temporal)

#### <a name="apidoc.element.temporal.clear"></a>[function <span class="apidocSignatureSpan">temporal.</span>clear ()](#apidoc.element.temporal.clear)
- description and source-code
```javascript
clear = function () {
  isProcessing = false;
  exportable.removeAllListeners();
  queue = {};
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.temporal.defer"></a>[function <span class="apidocSignatureSpan">temporal.</span>defer (time, operation)](#apidoc.element.temporal.defer)
- description and source-code
```javascript
defer = function (time, operation) {
  if (typeof time === "function") {
    operation = time;
    time = 10;
  }
  var task = new Task({
    time: time,
    type: type,
    task: operation
  });

  if (!isProcessing) {
    processQueue();
  }

  return task;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.temporal.delay"></a>[function <span class="apidocSignatureSpan">temporal.</span>delay (time, operation)](#apidoc.element.temporal.delay)
- description and source-code
```javascript
delay = function (time, operation) {
  if (typeof time === "function") {
    operation = time;
    time = 10;
  }
  var task = new Task({
    time: time,
    type: type,
    task: operation
  });

  if (!isProcessing) {
    processQueue();
  }

  return task;
}
```
- example usage
```shell
...
var temporal = require("temporal");

temporal.on("idle", function() {
  console.log("Temporal is idle");
});

// Wait 500 milliseconds, execute a task
temporal.delay(500, function() {

  console.log("500ms later...");

});

// Loop every n milliseconds, executing a task each time
temporal.loop(500, function() {
...
```

#### <a name="apidoc.element.temporal.loop"></a>[function <span class="apidocSignatureSpan">temporal.</span>loop (time, operation)](#apidoc.element.temporal.loop)
- description and source-code
```javascript
loop = function (time, operation) {
  if (typeof time === "function") {
    operation = time;
    time = 10;
  }
  var task = new Task({
    time: time,
    type: type,
    task: operation
  });

  if (!isProcessing) {
    processQueue();
  }

  return task;
}
```
- example usage
```shell
...
temporal.delay(500, function() {

console.log("500ms later...");

});

// Loop every n milliseconds, executing a task each time
temporal.loop(500, function() {

console.log("Every 500ms...");

// |this| is a reference to the temporal instance
// use it to cancel the loop by calling:
//
this.stop();
...
```

#### <a name="apidoc.element.temporal.queue"></a>[function <span class="apidocSignatureSpan">temporal.</span>queue (tasks)](#apidoc.element.temporal.queue)
- description and source-code
```javascript
queue = function (tasks) {
  var queue = new Queue(tasks);
  processQueue();
  return queue;
}
```
- example usage
```shell
...

// The first argument to the callback is the same as |this|
});


// Queue a sequence of tasks: delay, delay
// Each delay time is added to the prior delay times.
temporal.queue([
{
  delay: 500,
  task: function() {
    // Executes 500ms after temporal.queue(...) is called
  }
},
{
...
```

#### <a name="apidoc.element.temporal.repeat"></a>[function <span class="apidocSignatureSpan">temporal.</span>repeat (n, ms, callback)](#apidoc.element.temporal.repeat)
- description and source-code
```javascript
repeat = function (n, ms, callback) {
  return exportable.loop(ms, function(context) {
    callback(context);

    if (context.called === n) {
      this.stop();
    }
  });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.temporal.wait"></a>[function <span class="apidocSignatureSpan">temporal.</span>wait (time, operation)](#apidoc.element.temporal.wait)
- description and source-code
```javascript
wait = function (time, operation) {
  if (typeof time === "function") {
    operation = time;
    time = 10;
  }
  var task = new Task({
    time: time,
    type: type,
    task: operation
  });

  if (!isProcessing) {
    processQueue();
  }

  return task;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
