---
title: "Combine TrueCrypt bootloader and GRUB?"
date: 2008-02-06
forum: General Help
---

### Post by kaffelars on 2008-02-06
Today I have downloaded TrueCrypt 5, and find the possibility encrypt the entire system disk fascinating. However, as I dual boot Windows and Ubuntu, I have GRUB on the MBR. If I install the TrueCrypt bootloader I suppose GRUB will be erased.

My question is;** is it possible to use both the TrueCrypt bootloader and GRUB (or similar) to choose what OS to run ?** For instance, have TrueCrypt on MBR and then GRUB on the first partition?

Any suggestions (with explanations) will be appreciated :)

---

### Post by s0larian on 2008-02-06
If you install grub not into the MBR, but instead in an extra little /boot partition or to / and make with "sudo dd if=/dev/sdaX of=bootsect.lnx bs=512 count=1" a copy of the linux bootsector and copy it to c:\ in windows an make an entry to boot.ini in windows to boot Linux (i.e. c:\bootsect.lnx="Linux"), it should work.

---

### Post by kaffelars on 2008-02-06
Thanks a lot :)  
But I suppose this means I would have to reinstall Ubuntu?

---

### Post by mrsteveman1 on 2008-02-06
I could be wrong but it seems to me that with the TC bootloader installed, everything you boot must go through the windows bootloader first and then chainload from there.

However, it's my understanding that the WDE is limited to windows because the windows driver is involved once the system boots, and Linux is going to be completely unaware of how to root itself in this case.

---

### Post by mrsteveman1 on 2008-02-06
Now that I've tested a bit, I'm noticing that the TC bootloader can chainload partitions.

So for instance if you just encrypt the windows partition, when TC boots you can just hit esc and the bootloader can then boot other partitions (non encrypted).

So just make sure grub is installed correctly in the volume boot record of the linux partition.

---

### Post by nerd65536 on 2008-02-07
> **kaffelars said:**
> Thanks a lot :)  
But I suppose this means I would have to reinstall Ubuntu?

You won't need to reinstall Ubuntu, those steps can be preformed while booted from a LiveCD.

---

### Post by kaffelars on 2008-02-07
Sounds great :)
But:
I don't need a separate boot partition, do I?

Do I need to edit the TrueCrypt Bootloader, or is it enough to press Esc at boot?

---

### Post by zuczek on 2008-02-07
Hey, I also want to try the Truecrypt and encrypt my windows partition, but i'm not a experienced user of ubuntu so if anyone could please post some help (with commands :) ) how to move grub from mbr to linux partition so later i can install TC boot loader on mbr and make it work 
Thanks.

---

### Post by mrsteveman1 on 2008-02-07
The truecrypt bootloader can basically chainload other partitions by pressing ESC instead of entering your password.

So for instance if grub is installed correctly in the volume boot sector (the first part of a linux partition), then TC can chainload grub without any further configuration.

You can fairly easily install grub to the correct partition. Take careful note of the hd0,0 numbers you get with the find command and use them later on. 

```
sudo grub
```

Once grub loads, let it find the right partition and drive:

```
find /boot/grub/stage1
```

That last command should have returned something like (hd0,0) or (hd0,1)

So then you do:

```
root (hd0,0)
setup (hd0,0) 
```

Which should then give you a bunch of feedback about installing grub into the right place.

Once this is all done you also should not need to configure grub for windows, since the TC bootloader always loads first and can (must) load the windows bootloader itself.

Note that with linux installed you can only encrypt the windows partition and not the whole drive, because Linux cannot yet root itself when encrypted with TC like that.

---

### Post by zuczek on 2008-02-07
Thanks it worked :)

---

### Post by bkj1 on 2008-02-18
I am trying this setup as well but I cant boot anything but windows once truecrypt is installed.  My setup consists of a single drive with grub being installed to hd0,1.  Once truecrypt is installed and i hit the escape key truecrypt says no bootable partition found (or something to that effect).  Windows is able to boot.  What am I missing?

---

### Post by mrsteveman1 on 2008-02-18
The TC bootloader does some basic checking to see what partitions are bootable, so if there isn't any boot code in the linux partition TC cant boot into it.

Use the commands i posted in the older post in this thread to install grub to the linux partition, but keep your TC recovery CD handy if you need to use it.

---

### Post by bkj1 on 2008-02-18
Thats the thing my linux partition is hd0,1 which is where grub is installed but yet TC cant boot it.

---

### Post by mikko.ohtamaa on 2008-07-14
Here are my instructions how I got encrypted home and Truecrypted Windows Vista play nice together:

[http://blog.redinnovation.com/2008/07/15/perfect-dual-boot-crypted-hard-disk-setup-with-truecrypt-and-luks/](http://blog.redinnovation.com/2008/07/15/perfect-dual-boot-crypted-hard-disk-setup-with-truecrypt-and-luks/)

:KS

---

