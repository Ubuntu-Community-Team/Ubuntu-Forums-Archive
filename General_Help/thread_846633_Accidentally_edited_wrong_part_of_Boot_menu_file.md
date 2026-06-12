---
title: "Accidentally edited wrong part of Boot menu file"
date: 2008-07-01
forum: General Help
---

### Post by saikot on 2008-07-01
hi 
i'm facing a strange problem.i've edited the menu.lst file and 
unfortunately commented out the line titled ubuntu.as a result i can not hav access to ubuntu now.can anybody help me.plz reply.
thanks in advance

---

### Post by aysiu on 2008-07-01
Boot into recovery mode and then type ```
nano -B /boot/grub/menu.lst
``` and make your changes. Then save (Control-X, Y Enter) and ```
shutdown -r now
``` If you don't know how to boot into recovery mode, check out the first half of [this page](http://www.psychocats.net/ubuntu/resetpassword).

---

### Post by Spaceman9 on 2008-07-01
If I could give you a tip, after you get back into Ubuntu install QGRUBEditor from Synaptic. It has a GUI that makes it very easy to copy and edit menu.lst.

Also Super Grub Disk [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and System Rescue CD [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) can be very helpful if you need to rescue any linux distro.

---

### Post by drs305 on 2008-07-01
Another option when you get grub's menu.lst back: use the gui-based StartUp-Manager. It will edit the menu.lst without mistakes or manual editing.

[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Spaceman9 on 2008-07-01
drs305 you are a life saver! Do you know how long I've been looking for something that would make a rescue floppy? And it was there in Synaptic all along and I didn't know it! There's so much to learn about linux! Thank you very much for your post.

---

### Post by drs305 on 2008-07-01
> **Spaceman9 said:**
> drs305 you are a life saver! Do you know how long I've been looking for something that would make a rescue floppy? And it was there in Synaptic all along and I didn't know it! There's so much to learn about linux! Thank you very much for your post.

I really like StartUp-Manager but I have never actually used the 'rescue floppy' portion. 

Would you report back what it actually puts on the rescue floppy and how it works?

---

### Post by logos34 on 2008-07-01
Here's the standard grub boot floppy howto:
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

But Startupmanger sure makes it easier

---

### Post by Spaceman9 on 2008-07-01
drs305 Ok, booting with the rescue floppy went perfectly. It displayed the same GRUB menu that booting from my boot drive displays. I was able to boot Ubuntu (on my first drive) and my second distro (on my second drive).

In regard to what's on the floppy your guess is as good as mine. I tried Nuatilus in user and root mode and Krusader in user and root mode and konqueror and none of them could mount the floppy. All of them let me mount and see other floppies though. Whatever is on that rescue floppy doesn't want to be seen I guess. Any ideas why?


Thankx for the link logos34.

---

### Post by Spaceman9 on 2008-07-02
Drs305 ok, I used the Ubuntu 8.04 live cd to look at the rescue floppy. This is what's on it:

Boot folder          Lost+found folder

grub folder

default
device.map
e2fs_stage1_5
fat_stage1_5
installed-version
jfs_stage1_5
menu.lst
minix_stage1_5
reiserfs_stage1_5
stage1
stage2
xfs_stage1_5

---

