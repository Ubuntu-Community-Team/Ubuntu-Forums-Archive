---
title: "removing ubuntu from PC"
date: 2008-02-15
forum: General Help
---

### Post by richardy on 2008-02-15
Hi, 
I recently installed xubuntu gutsy on my laptop and had Xubuntu fiesty on a desktop. I now want to remove fiesty from the desktop and put windows on it so that i can sell it. I have had a few issues with  this in the past - what is the easiest way to do this. Any help would be much apreciated.

Cheers.

---

### Post by steveneddy on 2008-02-15
Put Windows CD in drive, restart, select "Install" when prompted.

Use entire disc to install operating system.

Sell PC.

 Go to laptop as quickly as possible.

:popcorn:

---

### Post by richardy on 2008-02-15
HI,
Thanks for replying. Yes i did that and it seemed to install fine except that now i seem to have a boot loader error. The error is as follows:
rootnoverify (hd0)

chainloader + 1

GRUB Laoding stage 1.5.

GRUB loading, please wait.....
error 22

After this it stops. Shouldnt the windows install have overwirtten the MBR?

Any ideas on how to get around this. I will see if i can find an old dos disk with Fdisk on it which should be able to rewite the MBR - actually can G-parted do this?

Your help is much apreciated.

Cheers.

---

### Post by bilge.tutak on 2008-02-16
I think during windows 98 era, I used to do something like
```
fdisk /mbr
```
with a startup disk
But I am not sure, so please check if it is the right thing.
The other approach could be deleting all the partitions so there is nothing left and then install MS.

---

### Post by richardy on 2008-02-16
Hi,
I think i have managed to fix it. Basically i used G-parted to force the system to boot from the first partition instaed of using the bootloader. This then allowed windows to complete its installation and overwrite the MBR with the correct information to boot windows which actually worked. NOw i can get on with the job of selling it. Thanks for your help.

Cheers.

---

