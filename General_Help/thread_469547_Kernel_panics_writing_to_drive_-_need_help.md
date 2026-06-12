---
title: "Kernel panics writing to drive - need help"
date: 2007-06-10
forum: General Help
---

### Post by stokkes on 2007-06-10
Hey there,

I've been getting some kernel panics writing/reading from one of my hard drives (500gb SATA) on /dev/sda2

Here's the error:
```
[46683.018116]
[46683.018118] HARDWARE ERROR
[46683.018119] CPU 0: Machine Check Exception:		4 Bank 4: b200000000070f0f
[46683.018147] TSC 556a9952579c
[46683.018155] This is not a software problem!
[46683.018164] Run through mcelog --ascii to decode and contact your hardware vendor
[46683.018179] Kernel panic - not syncing: Machine check
[46683.018289]
```

When i try to write to the drive or read to the drive. started happening a week ago. 

HOWEVER, before you say it's a drive/ram issue, let me mention this:

[LIST]
[*]All SMART tests return OK, no errors
[*]I can stream data from the drive over SAMBA to my MCE box/Mac laptop
[*]I can mount and read/write the drive in Windows XP using FS-driver ([www.fs-driver.org](www.fs-driver.org))
[*]Memtest86 was ran overnight, NO errors reported
[*]fsck'ing the drive returns no errors
[/LIST]

Here's my fstab entry for the drive:
```
UUID=e4fedd68-274d-4b69-8c54-156fadb91224 /media/videos ext3 defaults,acl,errors=remount-ro 0 1
```

Drive is currently on SATA3, I've tried putting it on SATA4, no dice. same thing.

My system specs:
Ubuntu 7.04 Server (64Bit Intel/AMD)
AMD 64 X2 (Opteron 170)
Asus A8N-E
2GB of Ram
nVidia 7800GT (nvidia driver is loaded in X)
3 HDs
 - 1x40GB boot drive (SATA)
 - 1x250GB storage/backup drive (SATA)
 - 1x500GB storage (SATA)

All other SATA drives are working fine.

Some other things:
the drive was originally formatted and set for ext3, however, the journal seems to have disappeared. trying to do a :
    tune2fs -j /dev/sda2
results in the same error as above.

Running the tests in XP, copying a file back and forth from the drive produces NO corruption, file hashes match perfectly.

I could **REALLY** use some help on this one, I've pretty much exhausted my options, even running different kernels, nothing seems to be working.

It COULD be the drive, but nothing makes me think it is, since file I/O operations on a different OS run fine without data corruption.

Thanks!

---

### Post by stokkes on 2007-06-10
**Update**

Mounting the drive with "-o ro" , read-only, I can copy files fine from the drive to another drive, no kernel panics

as soon as I mount the drive rw (default), and try to copy the exact same files, I get a kernel panic.

I'm **really clueless here**

Please help!

---

### Post by chmorgan on 2008-03-27
I'm seeing the same issue here on an epox 9npa+ ultra board with an nforce4 chipset. There is a post here, [http://www.gossamer-threads.com/lists/linux/kernel/885929](http://www.gossamer-threads.com/lists/linux/kernel/885929) that may indicate that the problem has been found and may be resolved in the near future.

---

