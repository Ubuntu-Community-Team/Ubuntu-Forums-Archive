---
title: "90-100% CPU usage for no reason????? 14.04"
date: 2014-07-23
forum: General Help
---

### Post by robert113 on 2014-07-23
A couple days ago I decided to install Ubuntu on an old laptop I had recently upgraded. 

Everything was going fine until my display broke. I plugged in to an external display and applied this fix, which seemed to work: [http://askubuntu.com/questions/198303/installing-ubuntu-12-on-a-dell-inspiron-1501-black-screen-with-vertical-color-li](http://askubuntu.com/questions/198303/installing-ubuntu-12-on-a-dell-inspiron-1501-black-screen-with-vertical-color-li)

However after I had done this I immediately noticed the OS was slow as mud. Sure enough my CPU usage was crazy high (90-100%) ALL THE TIME.

After a bit of searching I came across this bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1300393](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1300393)

I assumed that was what was affecting me so I decided to do a fresh install and start from scratch.

Again the OS worked perfectly for a while but after a couple reboots the problem came back. No external display was connected this time.

The only software I installed was that which the update manager did for me. And only other thing I do after each install is this fix to get my network devices running: [http://ubuntuforums.org/showthread.php?t=2154058](http://ubuntuforums.org/showthread.php?t=2154058)

Does anyone have any idea as to what might be causing the issue? Before this my CPU usage was between 10-15% and now it's breaking 90% constantly on both cores. When I type "top" into terminal the top two results are compiz and xorg.

Any help would be much appreciated.

---

### Post by TheFu on 2014-07-24
If the GPU driver doesn't off-load most graphics work, then the CPU must do it.  So, if you want lower CPU use, use a less-taxing GUI, which is NOT Unity. 
[http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/) explains how.

---

