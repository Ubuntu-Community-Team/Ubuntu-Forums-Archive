---
title: "How to umount drive after NTFS Configuration tool"
date: 2007-11-14
forum: General Help
---

### Post by evolving_monkey on 2007-11-14
Hello all,
How do you unmount a drive after mounting it with ntfs configuration tool?

---

### Post by callan79 on 2007-11-14
> **evolving_monkey said:**
> Hello all,
How do you unmount a drive after mounting it with ntfs configuration tool?


Hi,

In terminal :

```
sudo umount /media/XXX
```

(where XXX is the name of your mount point, like /media/disk, or /media/hdb1, etc)

Note that when you reboot it'll try to mount again as the NTFS tool puts an entry into your /etc/fstab file. To get rid of these entries :

```
sudo gedit /etc/fstab
```

and delete the offending lines, save, close and reboot!

Cheers
Callan

---

### Post by evolving_monkey on 2007-11-14
Callan,
Thank you for your reply. 

Unfortunately when I enter the command sudo umount /media/XXX (xxx = mountpoint) I get the error "command not found". I also tried replacing umount with unmount. It didn't work either.

I appreciate any further input you could offer.

Thanks for your time.

---

### Post by callan79 on 2007-11-15
> **evolving_monkey said:**
> Unfortunately when I enter the command sudo umount /media/XXX (xxx = mountpoint) I get the error "command not found". I also tried replacing umount with unmount. It didn't work either.

Hiya,

I've helped a number of friends locally with terminal commands, and the only time I've seen the command not found error was when one friend was typing:

    umount
--and--
   /media/xxx

with no space in between.

So you need to make sure you type this EXACTLY like this, and remember that Linux terminal commands are CaSe SenSiTive so you need to get it correct:

```

sudo (space) umount (space) /media/xxx

```

If you're getting "command not found" it means you're either messing up the "sudo" bit, or the "umount" bit

Let us know what you find

Cheers
CD

---

