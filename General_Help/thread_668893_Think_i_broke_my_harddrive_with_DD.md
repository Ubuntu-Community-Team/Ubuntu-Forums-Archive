---
title: "Think i broke my harddrive with DD"
date: 2008-01-15
forum: General Help
---

### Post by jonathany on 2008-01-15
Hey, 

I was trying to extract a .img file to an external hard drive, I looked around the forum and found a thread about using dd to extract it to a usb flash drive so i figured it'd work out the same. (stupid me i didn't check out what dd was used for or anything about it) so i followed the instructions and typed in something like

dd if=image.img of=/dev/sdb1

after typing that the terminal kinda froze and didn't show any output after a few minutes i closed it down. after my next reboot my usb hd isn't being mounted, and manual mounting doesn't work either. I tried it on 2 other machines 1 running windows xp and the other running ubuntu 7.10 aswell.

any ideas as to what is wrong would be appreciated. I should mention that lsusb does show the harddrive is connected. 

Thanks in advance

---

### Post by pjkoczan on 2008-01-15
dd does a bit-for-bit copy of a file to another file. I'm not quite sure of all the caveats but I do think I know what happened to you.

Specifying /dev/sdb1 as the output file means that the file is copied directly to the disk partition, not a file on said partition, starting at block 0, byte 0. You likely overwrote some important filesystem metadata on the disk when you did the straight copy, then when trying to remount the disk, the fs driver didn't know how to interpret the img file as metadata and said "I don't know what to do with this."

So, you will have to re-format /dev/sdb1. If you had other files on that partition, there may be ways to get them back, but don't count on it, and it will likely be tough.

I'm also confused as to why you think you needed to use dd. Is there any reason you couldn't just mount the USB disk's filesystem somewhere and copy a file under that mountpoint?

---

