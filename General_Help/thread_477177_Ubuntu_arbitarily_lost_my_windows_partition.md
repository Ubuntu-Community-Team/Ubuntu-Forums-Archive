---
title: "Ubuntu arbitarily lost my windows partition"
date: 2007-06-18
forum: General Help
---

### Post by The AlGorenator on 2007-06-18
Yes, as stated in the title - i was running my ubuntu happily, grabbing music and other files off my windows partition; then arbitarily, i booted up, and ubuntu doesn't realise there's a partition there - at all

i don't know why, and it saddens me - please help

running 7.04

---

### Post by scannerdarkly on 2007-06-18
do you get any error messages?  does your windows partition show up in grub?  need a little more info.

---

### Post by The AlGorenator on 2007-06-18
nope, nothing - it's asif it was never there - well, when i'm in ubuntu, anyway - i can, however, boot to it.

---

### Post by scannerdarkly on 2007-06-18
you lost me on the last part, can you mount the partition yourself via terminal?  if so it's still there.  Is your windows partition the first partition on the drive?  or did you install ubuntu first then Windows?  

Try putting this in your grub file:

title           Windows
root          (hd0,0)
savedefault
makeactive
chainloader         +1


The (hd0,0) might not be that for your partition so you need to figure out which partiton it is, 1, 2, 3, 4 or whatever.

---

### Post by The AlGorenator on 2007-06-18
oh, sorry - i mean, from the BIOS i can still boot windows, but ubuntu cannot detect the partition

where would one find teh grub file..again?

---

### Post by Brucevdk on 2007-06-18
If you can still boot to it then there's probably nothing to worry about. If Ubuntu doesn't seem to mount the Windows partition anymore perhaps  the manual configuration step in [HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)]("http://ubuntuforums.org/showthread.php?t=217009") could help.

That means installing ntfs-3g (if it isn't installed already) and updating */etc/fstab*.

---

### Post by The AlGorenator on 2007-06-18
i tried that, but it denied me permission :s any other ideas?

---

### Post by bigken on 2007-06-18
sudo apt-get install ntfs-config

---

### Post by scannerdarkly on 2007-06-19
> **The AlGorenator said:**
> i tried that, but it denied me permission :s any other ideas?

if you do a sudo gedit /etc/fstab then you shouldn't be denied or if you switch to root in terminal then you shouldn't get denied.


It's either sudo su or just su in ubuntu.....I can't remember i run Fedora, OpenSuse, and Ubuntu and they each have a few differences in there commands.

sudo mount /dev/sda# /mnt/whatever that should work in just mounting it.  And i agree install the ntfs driver so you can write on an ntfs partition.

---

### Post by The AlGorenator on 2007-06-19
Nope, even those commands won't work - if i look through my device manager, the partition is shown but the feild 'volume.ignore' is set to true - i think if i could fix that, it would work.

Any ideas how to change it?

---

