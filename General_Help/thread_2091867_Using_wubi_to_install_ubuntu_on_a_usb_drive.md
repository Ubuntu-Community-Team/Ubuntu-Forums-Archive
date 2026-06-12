---
title: "Using wubi to install ubuntu on a usb drive"
date: 2012-12-06
forum: General Help
---

### Post by LyTningB0LT on 2012-12-06
If I use wubi to install ubunto on my 8gb usb drive, will ubuntu have access to my hard drive, and will it modify or add anything there? I don't want ubuntu to change or add anything on my hard drive or, preferably, even have access to it.  How does that work?
 
Thanks in advance.

---

### Post by Frogs Hair on 2012-12-06
Wubi installations use the Windows boot loader so you may have to do some home work as to whether Wubi will work on a usb. It is possible to access the Windows file system from Ubuntu in a Wubi installation via the Ubuntu file manager.Also check the minimum space requirements for Wubi.  

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Mark Phelps on 2012-12-06
See  no point in using Wubi if that is going to be the only OS on that drive.  Wubi's main purpose is to prevent you from having to do partitioning.  If you're doing that anyway on a USB drive, you would do better doing a traditional install.

Also, if you are running Windows on your internal drive, then do NOT have it connected when you install to the USB drive to prevent accidentally writing GRUB to your Windows drive.

---

### Post by chadk5utc on 2012-12-06
If you wish to install to USB and use  the drive just for Ubuntu I suggest trying/using unetbootin it will take any iso or other disk image and install it to nearly any USB drive without issue.

---

### Post by LyTningB0LT on 2012-12-06
I got the impression that wubi was the easiest way to install ubuntu on a windows machine, but if unetbootin is better I'll look at that instead. How would I go about disconnecting my internal drive before installing? Sory for the noob questions.

---

### Post by verzx on 2012-12-06
To install it onto a pen drive I wouldn't use Wubi but use a Linux Live Key program such as the one below: 

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

This program is easy to use and good for running linux distributions without installing it on your hard drive.

---

### Post by 2F4U on 2012-12-06
If your machine is a desktop, open the case, look for the hard disc and disconnect the cable. If it is a notebook, turn it around and search for the screws which hold the hard drive. Unlock them and pull out the hard drive.

---

### Post by Tumshukuru H. Mhalila on 2012-12-06
it will not modify anything, but you have to be reasonable! it will run independently and you will be able to access all information from your hard disk

---

### Post by verzx on 2012-12-06
> **2F4U said:**
> If your machine is a desktop, open the case, look for the hard disc and disconnect the cable. If it is a notebook, turn it around and search for the screws which hold the hard drive. Unlock them and pull out the hard drive.

You don't need to do this if you just run it on a Live USB using LiLi. It will run from your Pen drive and not modify or even go near your hard drive. Just make sure you put the persistence as high as possible because that's the amount of information that can be stored etc. If you have any more questions feel free to PM me or use Google. :)

---

### Post by chadk5utc on 2012-12-06
> **LyTningB0LT said:**
> I got the impression that wubi was the easiest way to install ubuntu on a windows machine, but if unetbootin is better I'll look at that instead. How would I go about disconnecting my internal drive before installing? Sory for the noob questions.

No need to be sorry. The only foolish question is that which is unasked.
To clarify
If your installing to a Windows Machine and intend to keep windows
Wubi will do this I believe without changing the Windows partition I can not comment on this as I have never used it.

Second option is to Install a Dual-Boot which the install CD will handle. It will resize the partitions as needed/you choose.

If your installing to something like a USB thumb drive which is what I understood earlier then I would use unetbootin for this. Or any of the others suggested.

---

### Post by LyTningB0LT on 2012-12-06
I looked at unetbootin and saw that it creates a live USB instead of a full install.  Initially I assumed that a full install would be better, but after doing a little more research I read that it will wear down the usb faster because it's constantly reading/writing to the disk, instead of storing temp files in ram.  What are the disadvantages of a live USB versus a full install?

---

### Post by monkeybrain2012 on 2012-12-06
> **chadk5utc said:**
> If you wish to install to USB and use  the drive just for Ubuntu I suggest trying/using unetbootin it will take any iso or other disk image and install it to nearly any USB drive without issue.

Unetbootin doesn't install Ubuntu in a usb drive, it creates a live usb, which is limited in usage even with persistence. It uses FAT and is limited to 4 G as a result and you cannot upgrade system components such as kernel.

---

### Post by philinux on 2012-12-06
To create a bootable usb stick from windows see this.

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

---

### Post by monkeybrain2012 on 2012-12-06
> **LyTningB0LT said:**
> I looked at unetbootin and saw that it creates a live USB instead of a full install.  Initially I assumed that a full install would be better, but after doing a little more research I read that it will wear down the usb faster because it's constantly reading/writing to the disk, instead of storing temp files in ram.  What are the disadvantages of a live USB versus a full install?

Like I said, live usb is limited to 4 G persistence, you can't upgrade system components (or can't upgrade simply because you run out of space at some point), you can't install proprietary graphic cards (if you need them) etc. A full install uses Ext4 file system and it is a fully functioning Ubuntu installation. 

The reading/writing thing is an exaggeration IMO, if you have a modern, good usb flash drive it can survive for longer than 18 months with a full install(the life span of a non LTS Ubuntu release) I have done that before, write and rewrite and install different linux distros and the usb still work for 2+ years (I do so many read/write and rewrite that it is not normal usage). The real disadvantage is performance, if you install in a flash drive it is kind of slow (as oppose to a live usb which runs off ram), but you get the best performance if you install in an external hard drive instead.

When install, you don't have to remove the internal hard drive, just make sure you put the bootloader in the usb drive (/dev/sdb or /dev/sdc usually, /dev/sda is the internal hard drive) during installation (you choose where to install the bootloader on the same page with the partition layout, it is at the bottom of the page)

---

### Post by LyTningB0LT on 2012-12-06
I don't know if I want to invest in an external hard drive yet, so if there's that much difference in performance I think for the time being I'll just use a live usb.  Does it matter if I use Universal USB Installer or Unetbootin, or are they pretty much the same thing?

---

