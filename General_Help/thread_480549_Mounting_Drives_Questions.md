---
title: "Mounting Drives Questions"
date: 2007-06-21
forum: General Help
---

### Post by hypersire on 2007-06-21
Hi all -I have a few questions on mounting drives:

1) Any difference if you mount to /mnt as opposed to a dir in your home directory?

I mount my external drives to folders that I created inside my home directory. Quite often I will see instructions on mounting saying to create folders inside the /mnt directory.

Is there anything special about the /mnt dir? In other words, does it make a difference if you mount to /mnt or your home directory? 

The only thing I can think of is that programs might look inside the /mnt dir to see what's mounted (which wouldn't happen if you mounted to arbitrary folders in your home dir) ??

2) -t parameter

I often see people using this paramater when showing a mount command (e.g. mount /dev/scd0 -t iso9660 )

I never use this parameter and everything works fine, so I assume if you don't specify it automatically detects it?

Is it better to use it or not?

3) fstab

This file is only for devices that you want automatically mounted correct? It's better not to list any drives in here that aren't always connected right?

Thanks!

---

### Post by energiya on 2007-06-21
> **hypersire said:**
> 
1)
Is there anything special about the /mnt dir? In other words, does it make a difference if you mount to /mnt or your home directory? 

The only thing I can think of is that programs might look inside the /mnt dir to see what's mounted (which wouldn't happen if you mounted to arbitrary folders in your home dir) ??

I actually didn't even had a mount directory... at first I used /media but now I use /mnt. You can call it /bla if you want.

> **hypersire said:**
> 
2) -t parameter

I often see people using this paramater when showing a mount command (e.g. mount /dev/scd0 -t iso9660 )

I never use this parameter and everything works fine, so I assume if you don't specify it automatically detects it?

Is it better to use it or not?

Taken from the man page
> 
-t vfstype
              The argument following the -t is used to indicate the file  sys-
              tem  type. 


> **hypersire said:**
> 
3) fstab

This file is only for devices that you want automatically mounted correct? It's better not to list any drives in here that aren't always connected right?

Correct.

> **hypersire said:**
> 
Thanks!

You're welcome !

---

### Post by hypersire on 2007-06-21
Thanks energiya!

Regarding the "-t" parameter when mounting, I knew it specifies the filesystem type but I am wondering if there is any advantage to using it since it seems to automatically detect the file system if you don't specify it.

Maybe its purpose is to force a filesystem type if it is being detected incorrectly automatically?

---

### Post by energiya on 2007-06-22
I neved had to force the filesystem, it allways worked for me, so to avoid hurting my fingers ( :) ) I will use this only when I encounter a problem (or have to copy-paste). But I never had to mount something that wasn't prior defined in fstab. To mount a new device (let's say a new hdd or cdrom not defined in fstab) it would be wise to define the filesystem, just to be sure...

---

