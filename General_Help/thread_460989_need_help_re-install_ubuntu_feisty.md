---
title: "need help re-install ubuntu feisty"
date: 2007-06-01
forum: General Help
---

### Post by yohanes_chin on 2007-06-01
Hi all,

I just installed ubuntu feisty on my friend's notebook several days ago (make it dual-booting with windows xp), then he installed automatix & easyubuntu, but after knowing those programs not originally supported by ubuntu, he decide to reinstalled the ubuntu feisty so I help him by delete the partition and install it again.

Everything seems OK after the installation, but right now it seems there's something wrong, especially when adding/downloading software.  And I notice (maybe) automatix still there, by looking at Desktop - System - Administration - Software Sources - Authentication.  Here's the screenshot: [http://img2.freeimagehosting.net/image.php?540272d3cf.png](http://img2.freeimagehosting.net/image.php?540272d3cf.png)

Could someone give me better suggestion how to re-install it again. Anyway he still doesn't yet moving his files/data from his windows xp, so he doesn't have any important files on feisty, only some mozilla bookmarks and music files. Can he open those files again if I just backup from feisty on usb flashdisk?

Thanks.

---

### Post by uranous on 2007-06-01
Hey, i checked my authentication keys, they are like yours, so i don't think there is any problem with these. You said you have ''adding software'' problems, if you mean with your package manager, try this:

> **meng said:**
> Try opening a terminal and typing
sudo dpkg --configure -a
(you'll be asked to enter your USER password - make sure you type it and press Enter - the password will NOT echo to screen)
after this, try running package manager again.


I hope this help and that you don't have to reinstall your ubuntu...
P.S. I am a n00b, can't help u more :P but explain what your exact problem is, maybe someone have a solution without reinstalling

---

### Post by yohanes_chin on 2007-06-03
I hope this help and that you don't have to reinstall your ubuntu...
P.S. I am a n00b, can't help u more :P but explain what your exact problem is, maybe someone have a solution without reinstalling[/QUOTE]

sorry I think it was my misreading, I thought automatic is the same with 'automatic'. My friend's ubuntu can adding software properly now, looks like it just server downloading problem from where I live.

Thanks

---

