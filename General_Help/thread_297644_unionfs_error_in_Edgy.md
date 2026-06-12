---
title: "unionfs error in Edgy"
date: 2006-11-11
forum: General Help
---

### Post by Tonren on 2006-11-11
I had a script that mounted several folders as a single one using unionfs.  It worked consistently and fine in Dapper, but now that I've upgraded to Edgy, running the script produces this result:

```
mount: wrong fs type, bad option, bad superblock on none,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Checking dmesg:

```
[17186382.132000] unionfs_read_super: error while parsing options (err = -22)
```

This is the script:

```
sudo mount -t unionfs -o dirs=/home/mcantor/unions1=ro:/home/mcantor/unions2=ro none /home/mcantor/union
```

This is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=053c8815-3b5d-4ef0-a79f-95ec45b25202 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=0f0d95b4-3607-4e84-937d-c165bd9c94a0 /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=1B12E95309ED71AC /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=e4db8ab0-60c5-48f8-bda7-7167c1713a14 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/sdb1	/media/usbdisk	vfat	user,auto,fmask=0777,dmask=0000,uid=1000	0	0

```

Can anyone shed some light?

---

### Post by David_T on 2006-11-11
Possibly the unionfs module needs to be recompiled for use with the current kernel?  To do that you would probably want to uninstall unionfs and then run module-assistant to get new kernel headers and package source and recompile/reinst unionfs.  

I wanted to see if I could reproduce this, but during the build process in module-assistant, I started getting errors.  I didn't see a bug in Launchpad with this description, so I'm wondering if anyone else on Edgy can reproduce it.  This is just the part of the make ouput that started giving errors:


```

make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'         
  CC [M]  /usr/src/modules/unionfs/subr.o                               
In file included from /usr/src/modules/unionfs/fist.h:162,              
                 from /usr/src/modules/unionfs/subr.c:38:               
/usr/src/modules/unionfs/missing_vfs_funcs.h: In function &#8216;lock_parent&#8217;:
/usr/src/modules/unionfs/missing_vfs_funcs.h:27: error: &#8216;struct inode&#8217;  
has no member named &#8216;i_sem&#8217;                                             
/usr/src/modules/unionfs/missing_vfs_funcs.h: In function &#8216;unlock_dir&#8217;: 
/usr/src/modules/unionfs/missing_vfs_funcs.h:33: error: &#8216;struct inode&#8217; 
has no member named &#8216;i_sem&#8217;                                             
/usr/src/modules/unionfs/missing_vfs_funcs.h: In function &#8216;double_lock&#8217;:
/usr/src/modules/unionfs/missing_vfs_funcs.h:119: error: &#8216;struct inode&#8217; 
has no member named &#8216;i_sem&#8217;                                             
/usr/src/modules/unionfs/missing_vfs_funcs.h:119: error: &#8216;struct inode&#8217; 
has no member named &#8216;i_sem&#8217;                                             
/usr/src/modules/unionfs/missing_vfs_funcs.h: In function               
&#8216;double_unlock&#8217;:                                                        
/usr/src/modules/unionfs/missing_vfs_funcs.h:124: error: &#8216;struct inode&#8217; 
has no member named &#8216;i_sem&#8217;                                             
/usr/src/modules/unionfs/missing_vfs_funcs.h:124: error: &#8216;struct inode&#8217; 
has no member named &#8216;i_sem&#8217;                                             
make[4]: *** [/usr/src/modules/unionfs/subr.o] Error 1                  
make[3]: *** [_module_/usr/src/modules/unionfs] Error 2                 
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'     
make[2]: *** [unionfs2.6] Error 2                                       
make[2]: Leaving directory `/usr/src/modules/unionfs'                   
make[1]: *** [binary-modules] Error 2                                   
make[1]: Leaving directory `/usr/src/modules/unionfs'                   
make: *** [kdist_build] Error 2                                       

```

---

### Post by Tonren on 2006-11-16
So, has anyone else encountered this?  It's really bustin' up my productivity groove.  David_T, I don't really know how to use module_assistant in that way... could you explain the procedure?

---

### Post by mrintegrity on 2006-11-16
I just tried this my self, i get exactly the same vfs errors as the other poster, i also tried downloading the unionfs source for my kernel from the project page but that failed with other errors.

Anyone know how to fix thist? Is it some ubuntu patched unionfs thats causing it?

---

### Post by Tonren on 2006-11-26
Has anyone had any luck with this?  I'm jonesing for my organized file structures.

---

### Post by RAOF on 2006-11-26
Given that the error posted
```
[17186382.132000] unionfs_read_super: error while parsing options (err = -22)
```
is about parsing options, perhaps the unionfs options have changed?

In particular, browsing through the unionfs man page I see absolutely no indication that the "none" in your command is supported.  It looks like it should be replaced with "unionfs", as thusly:
```
sudo mount -t unionfs -o dirs=/home/mcantor/unions1=ro:/home/mcantor/unions2=ro **unionfs** /home/mcantor/union
```

---

### Post by Tonren on 2006-11-26
RAOF, unfortunately, that didn't work.  I'm still tinkering with it, but no luck yet.

---

### Post by Ibis on 2006-11-29
I'm keeping an eye on this thread, as I'm stuck with the same problem :/

EDIT: I found a solution! The leftmost must be RW, not RO :D Works for me now :P

---

### Post by Tonren on 2006-11-29
Good heavens!  Ibis, that worked for me, too.  Worked like a charm!  I can't fathom why that's the fix.  Well... hopefully a dev will catch this thread and be able to use it to fix things up.

---

### Post by RAOF on 2006-11-29
> **Tonren said:**
> Good heavens!  Ibis, that worked for me, too.  Worked like a charm!  I can't fathom why that's the fix.  Well... hopefully a dev will catch this thread and be able to use it to fix things up.

I guarantee a dev will **not** see this thread.  If this is a bug, post it to [launchpad.net](launchpad.net)!

---

