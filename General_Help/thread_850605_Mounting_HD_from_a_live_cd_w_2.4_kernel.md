---
title: "Mounting HD from a live cd w/ 2.4 kernel"
date: 2008-07-05
forum: General Help
---

### Post by MBro on 2008-07-05
I'm attempting to put XBMC on my old xbox to stream videos from my computer to the tv.

To get the softmod on the xbox I made a usb cable and have a supported CF card reader that xbox thinks is a memory card.

I need to get the splinter cell exploit save onto the memory card by using a xebian live cd with the 2.4 kernel.

Because xebian uses a modified vfat driver to read xbox drives I am only able to mount the CF card and cannot mount another usb drive.  My computer gets its internet wirelessly so I cannot download the exploit from the live cd (2.4 kernel).  

This leaves me with the only option of mounting one of my internal ext3 hard drives and copying the save from there.

I issued the commands 
# mkdir /media/hda
# mount /dev/hda2 /media/hda

only to get an error about /dev/hdb not being referenced in /etc/fstab

It's been a few years since I've dealt with fstab (thank god) so I'm a little unsure as to what to enter in it.  Especially with it being a live cd and a 2.4 kernel that I've never used before.

would adding a line 
```
/dev/hda2 swap swap defaults 0 0
```

Be all that is needed?

---

### Post by logos34 on 2008-07-05
I'm confused--is sda2 a data partition or swap?

sudo fdisk -l

you can try:

# mount -t ext3 /dev/hda2 /media/hda

/dev/hda[COLOR=Red]?[/COLOR] **none** swap **sw** 0 0

---

### Post by MBro on 2008-07-06
hda2 is actually a partition, my linux partitions are on hdb.  Just a weird way I did things when I installed linux while still using windows a few years ago.

---

