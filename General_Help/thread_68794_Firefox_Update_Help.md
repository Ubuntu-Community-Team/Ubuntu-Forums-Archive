---
title: "Firefox Update Help"
date: 2005-09-24
forum: General Help
---

### Post by xbilly on 2005-09-24
I am trying to upgrade my firefox to the new one and I am getting this message:

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

I am now unable to use my firefox at all. What is the problem?

---

### Post by kreek on 2005-09-24
I'm having the exact same problem and the exact same error message.
I also can no longer use firefox. Any help would be appreciated.

---

### Post by renev on 2005-09-24
Hi,

Exact same problem here. I think it started when updating to version 1.0.7.

Had to install Mozilla to surf the internet!!

I'm curious about the solution!!!


Gtz. ReneV

---

### Post by phex on 2005-09-24
Once I also had this problem. I deinstalled all mozilla firefox related packages like mozilla-firefox and this gnome-support stuff. Then i simple reinstalled the new version of mozilla-firefox. that was it. ;) 
here is an old thread how to deinstall and reinstall it.
[http://ubuntuforums.org/showthread.php?t=68532](http://ubuntuforums.org/showthread.php?t=68532)

if it is not functioning, then pls post here again. I will look at that problem in detail then.

---

### Post by Hobbsee on 2005-09-24
> **phex]Once I also had this problem. I deinstalled all mozilla firefox related packages like mozilla-firefox and this gnome-support stuff. Then i simple reinstalled the new version of mozilla-firefox. that was it.  said:**
> http://ubuntuforums.org/showthread.php?t=68532[/url]

if it is not functioning, then pls post here again. I will look at that problem in detail then.
 that definetly seems to be the solution

> sudo apt-get remove mozilla-firefox

sudo apt-get install mozilla-firefox

---

### Post by Goober on 2005-09-25
The quote in the last part of the above post worked, the bit about removing then installing mozilla-firefox, but you must restart.  

It restores Firefox with bookmarks and everything.  What happened anyway?  Was it to do with the name that messed things up?

---

