---
title: "dd always creates corrupted files"
date: 2014-04-12
forum: General Help
---

### Post by Edgar_Haener on 2014-04-12
Hello, 
I have been trying to write an image to an sd card/usb memory stick using the command line dd. I'm using Ubuntu 13.04, 64bit. 

I have first formated the sd card using gparted to 32-fat and then used
```
**dd bs=4M if=~/Desktop/2014-01-07-wheezy-raspbian.img of=/dev/sdb1**
```

once finished I run 
```
**sudo sync **
```
to flush the memory. 

However, this always produces a corrupt disk, both with an sd card as well as with a usb memory stick. What am I doing wrong?

(as an aside, is the a GUI way of doing this, given that ImageWriter doesn't exist for Ubuntu 13.04?)

Thank you,

---

### Post by sudodus on 2014-04-12
Welcome to the Ubuntu Forums :-)

First of all, ***dd*** is a very powerful command. It does what you tell it to do without questions, so if you tell it to overwrite (and destroy your files in the internal drive, that are not backed up) it will do it, even if you *intended* to do something else. So dd is nick-named 'disk destroyer'. You must double check and triple check the command line before running it.

To decrease the risk with dd, I made the shell-script ***mkusb***. See this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

-o-

Anyway, let us look at your task:

First of all, I would use ***sudo*** to have superuser privileges when running dd.

Second, you should check at the web site, from where you downloaded **[FONT=courier new]2014-01-07-wheezy-raspbian.img[/FONT]** what kind of image it is, an image of the whole drive, or an image of a partition. I think your problem is that it is an image of a drive, so the following command would work ***after unmounting all partitions on the target drive*** /dev/sdx

```
sudo dd bs=4096 if=~/Desktop/2014-01-07-wheezy-raspbian.img of=/dev/sdx
```

It is a good idea to run the ***sync*** command afterwards (like you did before).

My experience is that block size 4096 makes the flash process fastest in many computers. ***x*** is the drive letter, and it *must* be correct, otherwise you might overwrite valuable data, (maybe ***x***=b, maybe not).

If it is an image of a drive, you can rename it to 2014-01-07-wheezy-raspbian.iso and use mkusb to flash it (instead of using a risky dd command).

---

### Post by Edgar_Haener on 2014-04-12
Thank you for the fast reply, I will retry and make sure the drive is completly unmount as well as try to follow your guide using mkusb  as an alternative :-)[SIZE=4][SIZE=4][/SIZE][/SIZE]

---

### Post by Double.J on 2014-04-12
+1

if you're writing to make a bootable usb, something has to be at /dev/sdx. It gould be that you have already put a boot loader on the usb stick, or are copying/installing one separately. If you are just trying to copy a bootable iso file to the isb stick you have to dd it to the /dev/sdx. Otherwise the computer will not see it as a bootable disk.

Also check with the distributor that it can run from a usb. Last year i spent a whole sunday afternoon dd'ing a BSD image to usb and then zeroing out the usb, and trying again, redownloading the iso and checking the md5.... It was just built to boot from dvd.
in your case you have an img file, but the principle is the same - does raspian need a bootloader added as well, or do you have to update the boot-loader already one there?

Jj

---

