---
title: "Keyboard stops working &amp; X freezes"
date: 2008-05-25
forum: General Help
---

### Post by rampageoberon on 2008-05-25
I've noticed this happening 3 times now. When I reboot the OS once and then start a video X freezes and the keyboard is completely unresponsive. So I can not get it to restart X or do anything.

The video however keeps playing in the background and sound is audible but the display is frozen. The mouse is responsive, cursor moves but can not click on anything.

I can ssh into the box fine, but trying to restart gdm via ssh doesn't help. Trying to shut down the system makes the screen go all fuzzy and I have to cut power to the system.

Now after I restart for the second time everything is fine. Videos play perfectly. I really don't know what the problem could be as its running quite normally. Any ideas anyone?

Thanks
Jilan

---

### Post by rampageoberon on 2008-05-30
Any ideas anyone?

---

### Post by rampageoberon on 2008-06-28
any ideas please?

---

### Post by rampageoberon on 2008-08-18
I'm having this problem again and its happening quite repeatedly. My system seems to crash when I start a video. But after a hard reboot all is fine. It will play all videos now till the next time I reboot after which it will crash and the cycle continues.

I have no idea how to troubleshoot this, please help.

---

### Post by LunatikOwl on 2009-01-05
If I had a penny for each topic I posted and talked to myself on this forum...
I had the same problem and I just installed a newer intel driver from debian repos([http://packages.debian.org/sid/xserver-xorg-video-intel](http://packages.debian.org/sid/xserver-xorg-video-intel)). 
I did that after the comments on [bug 221316]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221316"). Please note the packages to remove and the xorg line to add. Even more, as a bonus, video is now more integrated with compiz:)

Hope this helps,
 
Cheers

---

### Post by abn91c on 2009-01-05
> **rampageoberon said:**
> I've noticed this happening 3 times now. When I reboot the OS once and then start a video X freezes and the keyboard is completely unresponsive. So I can not get it to restart X or do anything.

The video however keeps playing in the background and sound is audible but the display is frozen. The mouse is responsive, cursor moves but can not click on anything.

I can ssh into the box fine, but trying to restart gdm via ssh doesn't help. Trying to shut down the system makes the screen go all fuzzy and I have to cut power to the system.

Now after I restart for the second time everything is fine. Videos play perfectly. I really don't know what the problem could be as its running quite normally. Any ideas anyone?

Thanks
Jilan
disable desktop effects

---

### Post by rampageoberon on 2009-01-05
> **LunatikOwl said:**
> If I had a penny for each topic I posted and talked to myself on this forum...
I had the same problem and I just installed a newer intel driver from debian repos([http://packages.debian.org/sid/xserver-xorg-video-intel](http://packages.debian.org/sid/xserver-xorg-video-intel)). 
I did that after the comments on [bug 221316]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221316"). Please note the packages to remove and the xorg line to add. Even more, as a bonus, video is now more integrated with compiz:)

Hope this helps,
 
Cheers

Thanks very much for the link and help. I'll try out the suggestion and lets hope it fixes things.

:D

---

