---
title: "Ubunu Error 1 Message"
date: 2008-06-18
forum: General Help
---

### Post by victorash on 2008-06-18
I have installed Ubuntu 8.04 in Windows, and when I first booted and selected the option to boot into UBUNTU this error message comes up:

Error 1: filename must be either an absolute pathname or blocklist

Any ideas how I ca fix this ?

Thanks

---

### Post by cdtech on 2008-06-18
Are you using one drive for both OS's?

---

### Post by victorash on 2008-06-19
I have got to hard drives and it had been installed on my 2nd drive, so I tried installing it on my main drive, this time when I loaded up in Windows  XP Pro I used Wubi when I put my CD in (Ubuntu 8.04 iso386 on it) WUBI came up with the option screen , I selected to run Ubuntu within Windows it copied the information from the disk loaded up ok , when I re booted I had the Option of Booting into Windows or Ubuntu I selected Ubuntu it started to load then displayed the message:  

Booting UBUNTU 8.O4
Kernel 2.6.24-16-Generic 
Error 15 File not found

My Computer details are:
Windows XP Professional
intel(R) Core (TM)2 CPU
6400 @ 2.13Ghz
2.14 GHZ, 3.62 GB of Ram

Processors
2x Intel(R) Core(TM)2 CPU 6400@2.13GHZ

Thanks

---

### Post by realruntime on 2008-10-08
> **victorash said:**
> I have installed Ubuntu 8.04 in Windows, and when I first booted and selected the option to boot into UBUNTU this error message comes up:

Error 1: filename must be either an absolute pathname or blocklist

Any ideas how I ca fix this ?

Thanks

I had the same problem after an Ubuntu-Update. I did not install Ubuntu in Windows.

The problem was, that the /boot/grub/menu.lst was over 2000 lines long. The Ubuntu updater always messes up that file... I deleted everything but the Windows entry, the first four Ubuntu entries and the memtest entry.

I reinstalled grub (but I don't think this is necessary) and rebooted and all worked...

---

