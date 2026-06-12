---
title: "Mount HD problems..."
date: 2005-06-30
forum: General Help
---

### Post by ano1 on 2005-06-30
Hi,

I am trying to mount my hard drive so I can run to tests on it (need to run Cfdisk and Mke2fs). I created the dir /media/hda1 and then I tried sudo mount /dev/hda1 /media/hda1 . However it asks for the file system type. At the moment it is an unpartitioned HD. How do I go about mounting it (what spacific commands)? Also how do I know if it should be HDA, HDA1 or another HD* all together? Thanks for the help.

---

### Post by marsian on 2005-07-01
[QUOTE=ano1]Hi,

I am trying to mount my hard drive so I can run to tests on it (need to run Cfdisk and Mke2fs). I created the dir /media/hda1 and then I tried sudo mount /dev/hda1 /media/hda1 . However it asks for the file system type. At the moment it is an unpartitioned HD. How do I go about mounting it (what spacific commands)? Also how do I know if it should be HDA, HDA1 or another HD* all together? Thanks for the help.[/QUOTE]
 If I well understand, you want to partition your new disk, thus I guess that it is not yet formatted... In this case It will be difficult to mount it...
The good news is that you don't have to mount it to use fdisk.
The following link should be useful:
[http://www.knoppix.net/forum/viewtopic.php?t=3311](http://www.knoppix.net/forum/viewtopic.php?t=3311)

Note: the name of the disk depends of its physical position:
Primary Master- /dev/hda
     /dev/hda1 being the 1st partion
     /dev/hda2 the second, ...
Primary Slave- /dev/hdb
Secondary Master- /dev/hdc
Secondary Slave- /dev/hdd

---

### Post by ano1 on 2005-07-01
I tried cfdisk /dev/hda but it tells me I only have read access. When I view the info for the HDA it tells me it only has 649.80 MB of space. It should be a 120GB hard drive, so does this mean that there is a HD error or am I cfdisking the wrong location? I have also tried dev/hda1/ and get a FATAL ERROR: Cannot open disk drive. Any suggestions? Thanks a million.

---

