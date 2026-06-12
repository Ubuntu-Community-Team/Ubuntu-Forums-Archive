---
title: "No access to command line in UBUNTU 7.1"
date: 2008-03-13
forum: General Help
---

### Post by Kossilar on 2008-03-13
Hello,

I installed Ubuntu 7.1 on my girlfriend's laptop recently and she's been quite happy with how everything has turned out. I have too. Everything installed and worked perfectly on the first try with virtually no hick-ups, or hackery required to set things up.

However, my GF told me today that when she booted her system this evening she got nothing but a black screen with a flashing cursor in the top left corner. I figured this probably had something to do with the regular file system maintenance performed automatically by Ubuntu and an occasional command line screen refresh issue I've seen on my other system. 

However when I tried to show her how she could bring up the command line herself using CTRL-ALT-F* in order to trigger a screen redraw, I saw that the system wasn't providing command line access at all. Hitting CTRL-ALT-F1 just displays a black screen with a blinking cursor in one corner. 

This is slightly distressing, since if there are ever any problems with video on her system in the future, I'll have no way of fixing the problem for her beyond reformatting the system. 

Does anybody have any idea what's causing this problem and how it can be fixed?

---

### Post by taurus on 2008-03-13
If you think it's the graphic/video card, you can always reconfigure X server again.

Boot into recovery mode from GRUB menu and run

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by jakupl on 2008-03-13
Have you tried to wait for a while? 10-15 minutes mayby?

What is you labtop and hardware?

---

