---
title: "Can I edit an iso file and exchange some files?"
date: 2006-12-28
forum: General Help
---

### Post by jamaas on 2006-12-28
I need to exchange some files in an iso file for some cab files that I've edited to allow booting from usb stick.  Can anyone tell me if there is a program that will allow editing of the contents of an .iso?  I've tried kiso but it just gives an error and aborts.

Thanks
Jim

---

### Post by bernied on 2006-12-28
You can mount the .iso and read from it like so:
```
mkdir ~/tempiso
mount -t iso9660 -o loop /path/to/the/file.iso ~/tempiso
cd ~/tempiso
```
I don't know if the .iso file can be edited like this, but it would be easy enough to take a copy of the contents once mounted, make the changes, then rebuild the image. I haven't done this myself, but believe the command is makeiso

EDIT: The command is mkisofs. See [here](http://www.die.net/doc/linux/man/man8/mkisofs.8.html) for the man page

---

### Post by jamaas on 2006-12-29
Thanks Bernied, Happy Hogmanay!

> **bernied said:**
> You can mount the .iso and read from it like so:
```
mkdir ~/tempiso
mount -t iso9660 -o loop /path/to/the/file.iso ~/tempiso
cd ~/tempiso
```

I could open it but not edit it, so just unpacked the archive and did the exchange

I've also got mkisofs to work as well, fixed one small problem, the archive is more than 6 levels deep so had to use a -D option.  Now I have another, and for a newbie the man page is a bit big.  The iso I've created has filenames ending with :1 as in 
EXAMPLE1.IN_;1

I'm not sure if this will work correctly, any idea how to rebuit it and not produce the ;1 at the end?

Thanks a bunch.

Jim
I don't know if the .iso file can be edited like this, but it would be easy enough to take a copy of the contents once mounted, make the changes, then rebuild the image. I haven't done this myself, but believe the command is makeiso

EDIT: The command is mkisofs. See [here](http://www.die.net/doc/linux/man/man8/mkisofs.8.html) for the man page

---

