---
title: "Firefox 3b5 slapping my harddrive around"
date: 2008-04-28
forum: General Help
---

### Post by xdevnull on 2008-04-28
Why is FF3b5 beating my harddrive like a drum?  It doesn't always do it right away, but eventually it just slams it.  It slows the whole desktop down, peaking the CPU with I/O wait...and just writing and writing and writing to the HD.  I know this because I have activated several of the SysMon monitors.  It all goes away when I close firefox...once it finally dies.

I have tried to just run FF2 (which I am posting with), but have a problem with that.  I uninstalled the extensions I use from FF3, but I can't resinstall them under FF2.  I get an error 20 and have to check the console which enlightens me thusly:

Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938


Other than this cock-up Hardy has been pretty good for me.  Though the forums web site has been absolutely painful to use.  It has ground to a halt every time I've tried to search, and the response has been really slow, as if it were dropping packets like a sieve.

---

### Post by xdevnull on 2008-04-28
Finally able to do a better search; found this:
[http://ubuntuforums.org/showthread.php?t=759673](http://ubuntuforums.org/showthread.php?t=759673)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/215728](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/215728)

Turned of phishing detection; moved the urlclassifier files....seems to be working much better.  Hope this is fixed in the next update.

---

### Post by Absorbed on 2008-04-29
To save people from having to find the fix in the bug report, you turn off phishing/attack detection, close firefox, delete ~/.mozilla/firefox/[profile].default/urlclassifier*.sqlite, then open firefox again.

---

