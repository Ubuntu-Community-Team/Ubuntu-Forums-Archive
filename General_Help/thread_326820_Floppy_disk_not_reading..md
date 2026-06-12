---
title: "Floppy disk not reading."
date: 2006-12-28
forum: General Help
---

### Post by M_the_C on 2006-12-28
Hi,
  I'm trying to mount a flopy disk, I can normally mount them but I think it might have a strange file system\encrypted or something.

I get the:
mount: wrong fs type, bad option, bad superblock on /dev/fd0
error.

I've read through some other posts and it is not a problem with then fstab I don't think.

I tried blkid, it scanned and the just started a new blank line.  It didn't say anything.

Thank you in advance.

---

### Post by shrimphead on 2006-12-28
have you tried the disc in another PC at all? Floppies aren't known for their robustness after all

---

### Post by M_the_C on 2006-12-28
Checked in Windows and it does work.

It says that it is FAT fs.  I thought that worked in Ubuntu.

---

### Post by shrimphead on 2006-12-28
try something along the lines of
```
mount -t msdos /dev/fd0 /floppy
```

obviously substituting /dev/fd0 for your drive and /floppy for your mount location

---

### Post by M_the_C on 2006-12-28
No, sorry.

Still getting the error, 

I found on another page umsdos, but it said that didn't exist.  Do I need to load something?

---

### Post by wpshooter on 2006-12-28
I don't think you are going to be able to access that disk on your Ubuntu system with it having that format.

If your floppy has a compatible format it should automatically mount unless you have a VERY old un-updated version of Ubuntu.

Try formatting the floppy on your Ubuntu system to Ubuntu native format or take the floppy back to your Windows machine and try to format it with a RAW format.

---

### Post by M_the_C on 2006-12-28
Unfortunately that is not possible.  I am trying to install an old dos game using dosbox.

Thanks for the help everyone.  I think I'll try getting a blank floppy and copying the contents across.

---

