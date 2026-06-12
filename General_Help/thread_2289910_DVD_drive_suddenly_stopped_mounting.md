---
title: "DVD drive suddenly stopped mounting"
date: 2015-08-08
forum: General Help
---

### Post by lisasabina on 2015-08-08
Hey

DVD drive won't mount. I get this error message:

Error mounting system-managed device /dev/sr0: Command-line `mount "/mnt/ata-hp_CDDVDW_TS-U633J_R8666GRZA28303"' exited with non-zero exit status 32: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Not sure how to sort this.

---

### Post by ruzekle on 2015-08-08
I found this here:

[http://ubuntuforums.org/archive/index.php/t-1891405.html](http://ubuntuforums.org/archive/index.php/t-1891405.html)

```
the DVD still does not work, now I get this error message:

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

the output of dmesg | tail is:

tommy@tommy-desktop:~$ dmesg | tail
[  169.410950] VFS: busy inodes on changed media or resized disk sr0
[  169.417887] VFS: busy inodes on changed media or resized disk sr0
[  169.430233] VFS: busy inodes on changed media or resized disk sr0
[  169.460953] VFS: busy inodes on changed media or resized disk sr0
[  169.469391] VFS: busy inodes on changed media or resized disk sr0
[  169.474191] VFS: busy inodes on changed media or resized disk sr0
[  169.478392] VFS: busy inodes on changed media or resized disk sr0
[  169.484003] VFS: busy inodes on changed media or resized disk sr0
[  218.013929] UDF-fs: No anchor found
[  218.013938] UDF-fs: No partition found (1)


unless I am missing something, I think there should be an entry in fstab
for /dev/sr0 that tells the OS where the mount point is...yes???

as I suspected, there was no entry in /etc/fstab for the cd-rom....

[B]here is the fix I used:

code:

gksu gedit /etc/fstab

then I added this code after the last line in fstab

code:

/dev/sr0     /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

everything now works great...music cd's, data cd's, all dvd's....[/B]
```

---

### Post by lisasabina on 2015-08-08
Thanks for this, didn't solve my prob, must be doing something wrong... any other ideas?

---

### Post by pqwoerituytrueiwoq on 2015-08-08
does it only happen with this one disk?
it may be a bad disk

---

### Post by lisasabina on 2015-08-08
No, all disks. And on start up, it asks if I want to mount the drive manually or skip, when I try this, it comes up with that error.

---

### Post by pqwoerituytrueiwoq on 2015-08-08
try taking it out of /etc/fstab that should remove the error at boot
however assuming that fixes your drive after boot we can run a command in /etc/rc.local to get the job done

---

