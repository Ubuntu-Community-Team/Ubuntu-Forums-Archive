---
title: "formating a floppy disk for image dsk"
date: 2007-04-19
forum: General Help
---

### Post by bothosnx on 2007-04-19
Sorry, this may sound petty but couldn't find a command to format a floppy disk.

Other questions are, 

1. should i mount it first? if yes how... mount /dev/fd0 or /media/floppy0 or /mnt/floppy?
2. i'm actually trying to create an image for sbootmgr.dsk using dd command (dd if=sbootmgr.dsk of=/dev/fd0u1440... When i did this i didn't get any error but the disk won't boot. In fact when i browse the disk, it's empty.  

these were the results......
216+0 records in
216+0 records out
110592 bytes (111 kB) copied, 0.351865 seconds, 314 kB/s


Which is why i'm trying to format't first

---

### Post by bothosnx on 2007-04-19
I did the following command after copying an image...


root@Core2Duo:/media/floppy0# ls -l
total 0
root@Core2Duo:/media/floppy0# 

those were the results

---

### Post by Astinsan on 2008-05-18
unmount the disk then write to it.

---

