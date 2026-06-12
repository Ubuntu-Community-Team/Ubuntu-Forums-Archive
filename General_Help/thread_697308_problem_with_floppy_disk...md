---
title: "problem with floppy disk.."
date: 2008-02-15
forum: General Help
---

### Post by Mia_tech on 2008-02-15
I just inserted a floppy disk and my pc is not detecting it... I have created a mount point, /mnt/floppy, but I don't know the location of the floppy to mount it 

any help appreciated

---

### Post by amingv on 2008-02-15
```
sudo mount /dev/fd0 /mnt/floppy
```
Something along that line...

---

### Post by mbsullivan on 2008-02-15
Hi!

Amingv's code looks like it should work. If you want your floppy to be automounted upon bootup (or whenever you say "mount -a"), then try adding a line to the end of your /etc/fstab file.

Although I don't have a floppy drive to test it on, something like the following should work (I think... this will backup your fstab file anyway):

```
sudo cp /etc/fstab /etc/fstab.bak && sudo echo "/dev/fd0 /media/floppy auto rw,noauto,user,sync 0 0" >> /etc/fstab
```

Afterwards, if you want to play around with the mount options, just open /etc/fstab in a text editor (make sure to open it as root because of its permissions).

Cheers!
Mike

---

