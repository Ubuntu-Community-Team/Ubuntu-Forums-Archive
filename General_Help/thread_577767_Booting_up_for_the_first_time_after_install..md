---
title: "Booting up for the first time after install."
date: 2007-10-16
forum: General Help
---

### Post by Phaedras on 2007-10-16
Hey guys,

I just installed Ubuntu using Wubi for the first time.. Installation ran smoothly with no errors etc..

But then after i've rebooted to start up ubuntu for the first time i choose ubuntu instead of Windows vista and the ubuntu logo appear. Then it loads to about 30% and the screen goes black and then fades into a white screen with a black stripe at the bottom and at the top..

Any idea what is wrong?

My system is a duo 2 core t7500, geforce m 8600gt, 2gb ram etc..

Thanks in advance.

---

### Post by Ender77 on 2007-10-16
I am a total newb to linux/ubuntu, tried the gutsy alpha install, it also hangs at 30 percent installation.  

xp, intel 3 gig processor, 2 gig ram, 8600 ultra, 2 hard drives.

---

### Post by ago on 2007-10-16
Alt+F2
sudo dpkg-reconfigure xserver-xorg

select vesa driver

---

