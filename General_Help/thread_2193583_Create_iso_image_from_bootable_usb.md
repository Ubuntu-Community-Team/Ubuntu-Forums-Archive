---
title: "Create iso image from bootable usb"
date: 2013-12-13
forum: General Help
---

### Post by James Wilde on 2013-12-13
I just can't find any suggestions, neither on Google nor here, for how to create an iso image from a bootable usb stick.

I want to create a Windows 7 guest in Virtualbox from my bootable USB stick but you can't install a guest from USB.  So I want to create an iso image.

Anybody know how?

TIA

---

### Post by C.S.Cameron on 2013-12-13
I am quite sure I recall sticking .VDI's on a Flash drive and booting Vbox from them.
The VDI can then also be copied to any other computer running Vbox, (only 64bit to 64bit though).

---

### Post by James Wilde on 2013-12-14
Not quite sure how that will help me, CS.  My problem is to get the operating system from a usb onto the vdi drive.  I can find any number of ways to convert a bootable CD into a bootable USB stick, but when you've got the stick and no CD, going the other way is something none of the programs I have will handle.

Maybe I should create a bootable CD without finalising it and then copy the files from the USB stick.

---

### Post by cmcanulty on 2013-12-14
you can download from several web sites the windows image, as long as you have a valid key it is all legal and will install fine in virtual box

---

### Post by James Wilde on 2013-12-14
Thanks, CM.  I finally fixed it on of all things a Windows box using ImgBurn.

---

### Post by mikelavekkia on 2013-12-14
code "dd if=/dev/sdx of=usb.iso" 
where sdx you must insert correct location  of usb stik. the usb stik directcopy to usb.iso file

---

### Post by jimmyh1972 on 2013-12-17
whan usb is plugged in open terminal:
sudo fdisk -l
list of devides will apear - check for usb path (should be /dev/sd**x**)
than type dd if=/dev/sd**X** of=/home/MyBootableUsb.iso bs=4096 (bs stands for block size - how much data to write every second 4096 means about 4 mega in a second
you can type anything from 1024 and double it) its only an option if you wont type it it will just do it slower

---

