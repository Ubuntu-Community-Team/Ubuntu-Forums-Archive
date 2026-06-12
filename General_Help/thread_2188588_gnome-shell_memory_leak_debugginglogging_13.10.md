---
title: "gnome-shell memory leak debugging/logging 13.10"
date: 2013-11-18
forum: General Help
---

### Post by njKeats on 2013-11-18
I'm running Ubuntu Gnome 13.10 on my desktop. Ever since the update from 13.04 there is a very annoying memory leak. I know from my conky stats that gnome-shell is the culprit. And that it consumes about 1GB every 6 hours or so, minimum. Even when in standby mode! It is 100% reproducible. all I need to do is turn the computer on and in 2 days all my memory and swap is consumed. I have not checked to see if this happens on any other system, or on a clean USB boot. But the community seems content so I think it's just me.

How do I go about logging this so I can post a bug report? I know nothing about development for ubuntu, or even how things are developed in a community. But I would really like to identify this leak ASAP so a fix can be made. I'm not a complete beginner, but i have just never needed to debug my system before.

---

### Post by karsta62 on 2013-12-09
You're not alone. I have this issue as well with ubuntu 13.10 64bit and gnome-shell 3.8.4.
alt-F2 and "r" fixes it temporarily. Sometimes need to execute it several times. 
Just before I read your message my gnome-shell ate 3.8GB and after the reset only 269MB.

---

### Post by r_mano on 2014-01-16
In my case, the memory leak is greatly accelerated by using "sensors"extension (and "system monitor"). Removing them makes the leak much slower, but still there.

You can use alt-F2, yes, but then half of the time your gnome-terminal windows are transformed in ghosts... see [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1215798](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1215798)

I haven't be able to find links to see if the bug is worked on, or if it's fixed in shell 3.10. It surely didn't happen in  3.6.

---

