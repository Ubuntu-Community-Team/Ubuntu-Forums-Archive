---
title: "Ubuntu 8.04 Desktop Effects doesn't work"
date: 2008-07-03
forum: General Help
---

### Post by mostafamehiri on 2008-07-03
[CENTER][FONT=Comic Sans MS][SIZE=3][COLOR=RoyalBlue]Hello !!!
i am using Ubuntu 8.04
and i have Ati Radeon 9250 256Mb videoCard
but when i try to enable the Visual Effects on my computer
the screen becom all White ??!!
i dont know what to do ??
i'd downloeded Linux Ati deiver from the Ati website
but when i try to install it goes like this
[IMG]http://www.zshare.net/image/146420092d3da724/[/IMG][/COLOR][/SIZE][/FONT][IMG]http://img296.imageshack.us/img296/324/myfreakxj6.jpg[/IMG][/CENTER]

---

### Post by robertchahine on 2008-07-03
did you try that
```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install xserver-xgl

```

---

### Post by mostafamehiri on 2008-07-03
[CENTER][FONT=Comic Sans MS][SIZE=4][COLOR=RoyalBlue]No it didn't work
it's just made the PC slower
like broken when i move or open or close a window
and in the device manager it look like this[/COLOR][/SIZE][/FONT]
[IMG]http://img48.imageshack.us/img48/8245/myfreakmp5.jpg[/IMG]
[/CENTER]

---

### Post by Rocket2DMn on 2008-07-03
Your card does not support fglrx drivers, you should remove them.  If you downloaded the installer from ati's website, use that to remove them.  If you installed through Synaptic or apt-get, run
```
sudo apt-get remove --purge xorg-driver-fglrx
```
You should also remove xserver-xgl, that isn't used anymore for most cards
```
sudo apt-get remove xserver-xgl
```
Then see this thread for enabling compiz fusion on cards that use the open source "ati" driver (which is what you should be using) - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

