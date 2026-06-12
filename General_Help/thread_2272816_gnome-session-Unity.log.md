---
title: "gnome-session-Unity.log"
date: 2015-04-08
forum: General Help
---

### Post by Eglefino on 2015-04-08
Hello,

I have a large problem which I can't find a solution for it. There is a log-file (text/x-log) which keeps larger and larger until my /home of 10GB will be full and working with Ubuntu Trusty/version 'Gnome Flashback' isn't than not possible anymore. In the cache are a lot of logs, but one of them start as a small file of 15.0MB and in maybe 18 hours it's 8.6GB large. 

In my personal map with the path: home/eglefino/.cache/upstart/ I have the problems with "gnome-session-Unity.log", the second log in that cache has the same name but is a gzip. gnome-session-Unity.log.1.gz

Yesterday I thought I had found the solution by copy the log-file to another drive, but during asking a friend for a solution, the log became circa 200MB larger in 10 minutes. My friend gave me a link of the Ubuntu computer-tips, but those rules I did after installation of Trusty. And it did not help. In the small log-file were errors written about firefox, see the code.  Can I delete that log? Please help me!

 ```

console.error: autohddownload: 
  Message: TypeError: url is undefined
  Stack:
    @resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://jid1-tqvjxtbyha8qxg-at-jetpack/autohddownload/data/scripts/page.js:22:17
.each@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://jid1-tqvjxtbyha8qxg-at-jetpack/autohddownload/data/scripts/jquery.js:2:11774
e.prototype.each@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://jid1-tqvjxtbyha8qxg-at-jetpack/autohddownload/data/scripts/jquery.js:2:8302
@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://jid1-tqvjxtbyha8qxg-at-jetpack/autohddownload/data/scripts/page.js:20:9
onFire@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:149:11

console.error: autohddownload: 
Object
  - prototype Object
console.error: autohddownload: 
  Message: TypeError: url is undefined
  Stack:
    @resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://jid1-tqvjxtbyha8qxg-at-jetpack/autohddownload/data/scripts/page.js:22:17
.each@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://jid1-tqvjxtbyha8qxg-at-jetpack/autohddownload/data/scripts/jquery.js:2:11774
e.prototype.each@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://jid1-tqvjxtbyha8qxg-at-jetpack/autohddownload/data/scripts/jquery.js:2:8302
@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://jid1-tqvjxtbyha8qxg-at-jetpack/autohddownload/data/scripts/page.js:20:9
onFire@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/eglefino/.mozilla/firefox/cxvohcrc.default/extensions/jid1-TQvJxTBYHA8qXg@jetpack.xpi!/bootstrap.js -> res

```

---

### Post by Eglefino on 2015-04-11
Result of my question after two days: 158 views and 0 replies

I shall set my question at [SOLVED] (if I can find where to do that), because the problem is stopped by myself, by radically delete the 'gnome-session-Unity.log' from the ~/.cache. There was nobody who helped me with a (better) solution, so sometimes you have to take action without knowing it shall help or not. So I deleted the log and the problem didn't came back either :)).
[h=2][/h]

---

