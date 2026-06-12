---
title: "Totem problem"
date: 2005-08-23
forum: General Help
---

### Post by facefur on 2005-08-23
As a relative newbie, I'm lost.  I've tried to play and .mpg file with Totem, but all I get is a message: " Resource Busy or unavailable."  I've checked, and Totem is installed in /usr/bin, shows up as an executble,  permissions are set for everyone to execute (755), but even trying to run it directly from the directory gives the same message.

---

### Post by glug101 on 2005-08-23
Check out this post and see if it fixes the problem:

[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

esd is  a greedy little #$%^$# when it comes to /dev/dsp.  This howto helped me a lot!

---

