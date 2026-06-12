---
title: "Damaged filesystem"
date: 2008-03-01
forum: General Help
---

### Post by cyrus_the_virus on 2008-03-01
Hi,

This morning I turned on my laptop and booted from ubuntu 7.10. During the boot process it came up with a message that my partition contained errors and a check was forced. 
During the check all kind off errors occurred like *Buffer I/O error on device sda3, logical block 655429*. Eventually it concluded *An automatic file system check (fsck) of the root file system failed. A manual fsck must be performed*
I ran *fsck* manually which results in the same errors and a question if want to ignore that error :-?

I was able to mount the damaged partition from the livecd and rescue all my files to an usb disk. I also have windows installed and that works fine.
But I'm unable to boot in ubuntu normally (it does boot, but I only have a black screen with a console, so no X)

I could reinstall ubuntu because my files are save but that's a lot of work. So does someone as a solution for this??

Marty

---

### Post by pointone on 2008-03-01
You could run fsck -y; this causes fsck to answer "yes" to all the questions and can usually serve to repair most problems, though it may result in some data loss depending on the problem. A badblocks scan might be helpful, too.

---

### Post by cyrus_the_virus on 2008-03-02
Thanks :D

That worked! I've got my system up and running again. 

Marty

---

