---
title: "Gusty wont boot - disk cannot be found?"
date: 2007-10-25
forum: General Help
---

### Post by ninocass on 2007-10-25
Hi

My gusty install has been working grand for the past few days, however i have the following problem

when i boot in recovery mode i get:
```

waiting for root file system........
Done
    Check root= bootarg cat /proc/cmdline
    or missing module, devices: cat /proc/module ls /dev
ALERT! /dev/disk/by_uuid/<numbers> does not exist Dropping to a shell

```

then i get a busybox prompt

Any ideas?

Thanks
Nino

---

### Post by nacho32 on 2007-10-25
if you access to a pc I suggest you download and burn the super grub [boot loader]("http://www.linux.com/articles/57240"), a must have

---

### Post by logos34 on 2007-10-25
you can try this:

-hit 'e' to edit recovery entry, hit 'e' again on the 'kernel' line and replace

..**.root=UUID=xxxx-xxxx**...

with this format:

...**root=/dev/sda1**

or whatever your root partition is

---

