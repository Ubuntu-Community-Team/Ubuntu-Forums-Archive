---
title: "Is Chromium hijacking Firefox?"
date: 2015-08-14
forum: General Help
---

### Post by MoebusNet on 2015-08-14
For about a week now when I boot up my PC and click on the Firefox button in Unity to open Firefox, it does not respond. Waiting and reclicking does nothing. If I open a Terminal window and type in the command 'firefox' this is what I get:

```
I@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:2:12261
P@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:2:11615
n@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:2:5297
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
pbs<@resource://unity/observer.js:38:71
Observer.prototype.observe@resource://unity/observer.js:77:24
TabsProgressListener.onStateChange@chrome://browser/content/browser.js:15500:9
callListeners@chrome://browser/content/tabbrowser.xml:538:24
_callProgressListeners@chrome://browser/content/tabbrowser.xml:559:13
mTabProgressListener/<._callProgressListeners@chrome://browser/content/tabbrowser.xml:596:22
mTabProgressListener/<.onStateChange@chrome://browser/content/tabbrowser.xml:752:1
O@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:1:22106
h@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:1:18928
Mn@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:4:29096
Pn@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:4:24718
Fn@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:4:31059
h@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:1:2406
z@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:2:15250
I@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:2:12261
P@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:2:11615
n@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:2:5297
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
pbs<@resource://unity/observer.js:38:71
Observer.prototype.observe@resource://unity/observer.js:77:24
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
pbs<@resource://unity/observer.js:38:71
Observer.prototype.observe@resource://unity/observer.js:77:24
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
pbs<@resource://unity/observer.js:38:71
Observer.prototype.observe@resource://unity/observer.js:77:24
TabsProgressListener.onStateChange@chrome://browser/content/browser.js:15500:9
callListeners@chrome://browser/content/tabbrowser.xml:538:24
_callProgressListeners@chrome://browser/content/tabbrowser.xml:559:13
mTabProgressListener/<._callProgressListeners@chrome://browser/content/tabbrowser.xml:596:22
mTabProgressListener/<.onStateChange@chrome://browser/content/tabbrowser.xml:752:1
h@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:1:18904
h@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:1:2406
E@https://s.yimg.com/rq/darla/2-8-9/js/g-r-min.js:2:15025

```

I ask only because the output mentions a 'chrome listener'.

Anyone have an idea what's going on?

---

### Post by v3.xx on 2015-08-14
This looks similar

[http://ubuntuforums.org/showthread.php?t=2290531&p=13337947#post13337947](http://ubuntuforums.org/showthread.php?t=2290531&p=13337947#post13337947)

---

### Post by MoebusNet on 2015-08-14
Thanks! I'll try it out.

---

