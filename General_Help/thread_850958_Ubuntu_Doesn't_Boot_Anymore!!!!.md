---
title: "Ubuntu Doesn't Boot Anymore!!!!"
date: 2008-07-06
forum: General Help
---

### Post by thedudething on 2008-07-06
I've been using Ubuntu for a long time, love it. I installed it from Wubi 8.04 from XP, but then it suddenly froze and I had to turn off my computer by hand. Now if I choose Ubuntu from the boot menu, it tells me "find --set root --ignore-floppies /ubuntu /install/menu.lst" and it won't find it. I can't find menu.lst on Windows. Is there anyway to fix Ubuntu without losing the files I had in the home folder?

---

### Post by ago on 2008-07-06
run chkdsk /r from windows and check whether you have some hidden found000 file laying around in C:\ or C:\ubuntu

---

### Post by thedudething on 2008-07-07
No, I didn't find that. Is there any way of creating a new menu.lst?

---

### Post by ago on 2008-07-07
the important thing is whether you have /ubuntu/disks/root.disk or not, the other files are replaceable

---

### Post by thedudething on 2008-07-07
How do I check that?

---

### Post by ago on 2008-07-07
In windows you should have a file c:\ubuntu\disks\root.disk of several GB that is the virtual disk. Replace c: with whatever drive you installed ubuntu into

---

### Post by thedudething on 2008-07-07
I've never had a folder called /ubuntu/disks

---

### Post by ago on 2008-07-07
If you did finish the installation (linux side) and were able to login into ubuntu with your username and password, you must have had one.

---

### Post by thedudething on 2008-07-07
Yes I was able to before.

---

### Post by thedudething on 2008-07-07
The only folders on /ubuntu are docs, install and winboot

---

### Post by ago on 2008-07-07
Then check again for found000 hidden files. You can also check whether all disk space is accounted for. You might need some recovery tool to restore ubuntu/disks

---

### Post by thedudething on 2008-07-07
What if I just made a new menu.lst?

---

### Post by ago on 2008-07-08
there is no point if you cannot recover /ubuntu/disks/root.disk

---

### Post by thedudething on 2008-07-08
So how can I do that?

---

### Post by ago on 2008-07-08
You probably need windows file recovery tools

---

### Post by thedudething on 2008-07-08
Hey, I found a folder called found.000. What do I do with it?

---

### Post by ago on 2008-07-08
Either use recovery tools or (suboptimal) manually extract the files within that in their original place.

---

### Post by thedudething on 2008-07-08
How do I do that?

Edit: Where can I find the recovery tools?

---

### Post by thedudething on 2008-07-08
O and I can't move the files, it's not letting me.

---

### Post by ago on 2008-07-08
See if you can copy them, the important one is root.disk

---

### Post by thedudething on 2008-07-08
I copied them before, but it didn't fix it because I think I put them in the wrong places. So I copied them back and now I cannot copy them again.

---

### Post by thedudething on 2008-07-09
I can move the files now, so now what?

---

### Post by thedudething on 2008-07-09
Well I created a folder called "disks" under ubuntu and copied root.disk and swap.disk to it. Also copied boot to /ubuntu/install and i copied shared to /ubuntu. I tried booting into ubuntu again and I got this:

Booting 'Ubuntu 8.04, kernel 2.6.24-16-generic'
Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-16-generic root=VVID(UUID?) =04C0A8CAC0A8CZFZ loop=/ubuntu/disks/root.disk ro quiet splash
Error 15 File not found

What now?

---

### Post by plastichero on 2008-07-09
From windows, after running the WUBI installer, replace "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and reboot. Hope it works. (Here G: was the drive that Iselected, it may be different for you)

Also, make your windows drives NTFS formatted.

---

### Post by thedudething on 2008-07-09
I edited menu.lst, same thing happens.

---

