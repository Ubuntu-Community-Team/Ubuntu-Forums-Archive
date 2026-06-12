---
title: "Need help with boot failure"
date: 2008-03-06
forum: General Help
---

### Post by petros85 on 2008-03-06
Guys please help I'm a beginner and i think i messed up. I followed the instructions found here [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) to install the ricoh drivers for my vaio FZ21M webcam. The make install and the modprobe had permission problems so i used sudo in front of these and everything seemed fine.Except of course that the camera didnt work.The REAL problem is that now my system cannot boot!!!I get continuous messages like these:
```
[ 2750.208000] r5u870-0: command a0[246] failed: -71
[ 2750.208000] r5u870-0: initialization failed: -71
```
Its just this message over and over again and it doesn boot.The grub menu at the beginning appears normally but after that it stucks.PLEASE HELP i don't want to install the webcam anymore just to save my system!

---

### Post by petros85 on 2008-03-06
Can someone help me please?? I booted from live cd.How do i kill the stupid r5u870 insallation that i did and is causing the problem???

---

### Post by petros85 on 2008-03-07
Come on!Anyone?Please tell me a way to boot and restore.I don't want to reinstall!

---

### Post by murataht on 2008-03-07
I hope this can be of some help.

Personally, I don't understand what those messages mean. But I have an idea maybe works:

if you have a linux-boot-disk, i mean a ubuntu-installation disk, you can boot from cdrom. 
Now, you can see your heard disk, and re-install/fix grub on your hard disk...

hopefully this is useful. and if it works let us know.

good luck

[EDIT]

Maybe you need to unload the driver you have installed for the webcam. but I don't know how to do it from the cdrom-booted system. 
Does anyone know? thanks.

---

### Post by petros85 on 2008-03-07
well this is what i tried to do.I boot from my installation disk and i try to find that stupid r5u870 module to remove it or to blacklist it or something.The problem is that i dont have permission in the important files.I cant delete anything!

---

### Post by murataht on 2008-03-07
Can't you use "sudo" in your cdrom-booted system???

---

### Post by modafokaxx on 2008-03-19
Hey, I've just run into the same problem. I followed the same set of instructions..

Apparently, the r5u870 module causes some sort of problem at startup.
But, even though it looks like the system hasn't booted, it actually works.

So get a terminal window (ctrl+alt+F1), log in, and unload the module:
```
sudo modprobe -r r5u870
```

It should stop the endless loop of error messages and bring you to the gdm login screen!

Hope that helps...

---

