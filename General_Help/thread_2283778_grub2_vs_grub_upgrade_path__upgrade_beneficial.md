---
title: "grub2 vs grub: upgrade path ? upgrade beneficial ?"
date: 2015-06-24
forum: General Help
---

### Post by Cbhihe on 2015-06-24
Hi to everybody,
[Running Trusty desktop 14.04.2 with linux-image-3.16.0-41-generic 3.16.0-41.57 on a dual boot Win /Lx x86_64 machines.]

I "discovered" recently that I use grub (legacy) instead of grub2 which seems to be all the rage these days. Fewer recent post on grub than on grub2.
What is the difference between the two grub versions ?
Is there an upgrade path and is it beneficial to carry out such an upgrade ?
Thanks.
-ced.

---

### Post by dino99 on 2015-06-24
trusty with grub (aka grub legacy) is not the default bootloader; so it seems an oldish installation been dist-upgraded multiple times.
hopes you do some system cleaning (clean/autoclean/autoremove/gtkorphan) from time to time. And glance at possible broken links inside the /etc/rc?.d/ folders.

Grub (grub1/grub legacy) is deprecated: no more upstream activity, only possible fixes, but nothing done since early 2012 ;)

So, if you does not do a fresh install, you can purge the actual grub and menu.lst (not compatible with grub2), then install grub2

> sudo apt-get purge grub*
sudo apt-get remove menu.lst
sudo apt-get install grub-pc

when asked, install it on /dev/sda

---

### Post by oldfred on 2015-06-24
Many versions ago, there was an upgrade path. It had grub legacy and grub2 installed. And then from grub legacy you could boot grub2 to show that it worked and then if you liked it could convert.

Do you still have a grub2 entry or did they stop that?

Boot-Repair now has the grub purge & reinstall as one of its advanced options.
Or you should just be able to run the purge & reinstall of grub2. Make sure Internet is working as you can purge and then cannot boot, but it has to download new packages to install grub2.

       # kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)
# HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

    
       # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by grahammechanical on 2015-06-24
There is this command

```
grub-probe -V
```

This is what I get

> graham@sdb1-Uplus1:~$ grub-probe -V
grub-probe (GRUB) 2.02~beta2-26ubuntu1


The benefits? Recovery mode and all the previous kernels are put in a sub-menu called Advanced options for Ubuntu. Which makes the presentation of the boot menu options much neater.

The Grub configuration file should not be edited by us. It is composed from several other files that we can edit. It gives us a way of customising the boot menu with less risk of us messing up the boot loader process. If we know what we are doing, that is. :)

Regards

---

### Post by Cbhihe on 2015-06-25
Thanks @dino99, @oldfred, @grahammechanical.
I will get back to this thread tomorrow. I have been away for two days.

---

### Post by Cbhihe on 2015-06-26
Update complete!
```
$ grub-probe -V
grub-probe (GRUB) 2.02~beta2-9ubuntu1.2
```

I checked that the boot menu is now:[INDENT]Ubuntu
    Advanced Option for Ubuntu (sub menu are the latest kernel-image and the previous one along with some sort of debug version for each)
    Memory Test (memtest86+)
    Memory Test (memtest86+ serial console 115200)
    Microsoft Windows XP Professional (on /dev/sda1)[/INDENT]

Thank you very much again @dino99, @oldfred and @grahammechanical.
Great help and docs on a topic where being sloppy can be painful.

---

