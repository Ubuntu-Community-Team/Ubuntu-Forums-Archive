---
title: "My swap is gone!"
date: 2007-01-13
forum: General Help
---

### Post by zergberg on 2007-01-13
Recently I've noticed that I no longer have a swapfile! This is great fun and does wonders for stability. I'm not entirely sure where it went but the partition is still there. Any idea how to get it back?

My fstab looks like this, though I mucked around with it some. (Swap didn't work before then either.)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>		<type>  <options>					<dump>  <pass>
proc		/proc			proc    defaults					0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=2dee5a03-f775-4bb2-a199-36782a858c69 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb7 -- converted during upgrade to edgy
UUID=14bfb50e-ebe5-4884-9e50-c9e35be9def0 /home/fivre ext2 defaults 0 2
# /dev/hdb5 -- converted during upgrade to edgy
UUID=f9e32149-5e0d-4f83-8689-7e0b03d3293b /home/fivre/a_august ext2 defaults 0 2
# /dev/hdb8 -- converted during upgrade to edgy
UUID=485203c6-9082-41a6-93a0-ddc40ecf9409 /home/fivre/a_june ext2 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=278b2e3a-f5cd-48e4-806f-6a33248fa0ed /home/fivre/a_may ext3 defaults 0 2
/dev/hda1	/media/winnt		ntfs    defaults,nls=utf8,umask=007,gid=46,noauto	0       1
/dev/hdb6	/media/winprog		ext2    defaults,noauto					0       2
# /dev/hdb3 -- converted during upgrade to edgy
/dev/hdb3	swap			swap	pri=42			0	0
/dev/hdc	/media/cdrom0   		udf,iso9660 user,noauto				0       0

```

---

### Post by dcstar on 2007-01-13
> **zergberg said:**
> Recently I've noticed that I no longer have a swapfile! This is great fun and does wonders for stability. I'm not entirely sure where it went but the partition is still there. Any idea how to get it back?

My fstab looks like this, though I mucked around with it some. (Swap didn't work before then either.)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>		<type>  <options>					<dump>  <pass>
proc		/proc			proc    defaults					0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=2dee5a03-f775-4bb2-a199-36782a858c69 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb7 -- converted during upgrade to edgy
UUID=14bfb50e-ebe5-4884-9e50-c9e35be9def0 /home/fivre ext2 defaults 0 2
# /dev/hdb5 -- converted during upgrade to edgy
UUID=f9e32149-5e0d-4f83-8689-7e0b03d3293b /home/fivre/a_august ext2 defaults 0 2
# /dev/hdb8 -- converted during upgrade to edgy
UUID=485203c6-9082-41a6-93a0-ddc40ecf9409 /home/fivre/a_june ext2 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=278b2e3a-f5cd-48e4-806f-6a33248fa0ed /home/fivre/a_may ext3 defaults 0 2
/dev/hda1	/media/winnt		ntfs    defaults,nls=utf8,umask=007,gid=46,noauto	0       1
/dev/hdb6	/media/winprog		ext2    defaults,noauto					0       2
# /dev/hdb3 -- converted during upgrade to edgy
/dev/hdb3	swap			swap	pri=42			0	0
/dev/hdc	/media/cdrom0   		udf,iso9660 user,noauto				0       0

```
Use gparted to verify a Swap partition exists, then look at:
```
man swapon
```

---

### Post by raul_ on 2007-01-13
That happened to me once...i just "created" a new one in the same file.

---

