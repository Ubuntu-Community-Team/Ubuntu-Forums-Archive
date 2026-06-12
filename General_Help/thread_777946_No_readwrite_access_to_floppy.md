---
title: "No read/write access to floppy?"
date: 2008-05-01
forum: General Help
---

### Post by jorwex on 2008-05-01
Hey all,

trying to revive an old floppy disk. I had no idea how to start a floppy drive from scratch in linux, so I did some reading. This is what I ended up with:

sudo umount /media/floppy0
fdformat /dev/fd0
mkfs -t vfat /dev/fd0 1440
sudo mount /dev/fd0 /media/floppy0

then I couldn't write to it unless i was root. im using the floppy to load sata drivers onto a windows xp installation for a friend, so i dunno...maybe if its only writable by root, thats finee.

but anyway, i tried:
sudo chmod 777 /media/floppy0

and that went through without any errors (here's the verbose output: "mode of `/media/floppy0' changed to 0777 (rwxrwxrwx)") 

But I still couldn't write to it. I even tried launching a root nautilus window and tried right clicking on the drive and changing the permissions but it wouldnt let me. it would gimme an error after I changed any of the drop down menus.

Any ideas? should i just shut up and do the windows thing as is? this is bothering me...

using hardy btw. 

thanks for reading!

---

