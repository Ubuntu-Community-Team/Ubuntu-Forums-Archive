---
title: "GRUB not working right"
date: 2007-12-29
forum: General Help
---

### Post by VChief on 2007-12-29
Ok, I just reinstalled everything after starting from scratch by wiping my hard drive. Everything's working ok except...GRUB. I have Ubuntu on my 2nd hard drive and it was the last distro I installed so I used Ubuntu's GRUB install. The GRUB menu comes up, but no matter what you select, it says file not found. Now, if I boot up the install CD and select "Boot hard disk" GRUB works from there just fine. Any ideas what's up?

---

### Post by TidusBlade on 2007-12-29
Heard loads of good things and how it fixes thing, so try out the [Super GRUB disk](http://supergrub.forjamari.linex.org/).

---

### Post by VChief on 2007-12-29
Unfortunately, that didn't work. Here's what I'm getting:

For Ubuntu and Arch: Error 17
For XP: Error 13
For Debian: Error 15

I'm confused! I admit, I know nothing about GRUB. I did run fdisk -lu and found that the Ubuntu partition didn't have a bootable flag. Fixed that but I still need the LiveCD to get GRUB to work.

---

### Post by teryowen on 2007-12-29
try bootin up into a live cd and in terminal:

sudo grub
root (hdX,Y)
setup (hdZ)
quit

where X is the hard drive for your ubuntu so if its the 1st hard drive would be 0 if its the 2nd hard drive would be 1, so 1 for X.
where Y is the partitions for your ubuntu so if its the 1st partitions y would be 0 if the 2nd then y would be 1 and so on change the value accordingly.
as for the Z value try the number 1 for the 2nd hard drive if its doesnt work try the process againa and replace Z with 0. see wat that gives u?

---

### Post by meierfra on 2007-12-29
For detailed help, boot from the Ubuntu LiveCD.

Go to Places->Computer and double click the Ubuntu partition. (This mounts your Ubuntu partition.)

Post the output of 

```
sudo fdisk -l
```

and

```
cat /media/disk/boot/grub/menu.lst
```

(all "l" are lower case L, not the number one)

---

