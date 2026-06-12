---
title: "Ubuntu 22 unable to mount exFAT hard drive?"
date: 2023-06-09
forum: General Help
---

### Post by Hibari on 2023-06-09
Hi, this is probably a silly issue but my Ubuntu won't mount the external disk anymore, instead it gives the following error:

[IMG]https://files.catbox.moe/hchv3d.png[/IMG]


Trying via terminal does not work either.

```
sudo mount /dev/sda1 /mnt
mount: /mnt: unknown filesystem type 'exfat'.

```

I have exfat-fuse and exfatprogs installed, in case you were wondering.

Thank you in advance.

---

### Post by Bashing-om on 2023-06-09
Hibari; Hello

Admittedly, I do not know a lot about Windows' file systems - however from my notes:
appears that one must also have  exfat-utils installed.

What happens when you explicitly tell the system to mount exfat ?
Like so:
```

sudo mount -t exfat -o umask=000 /dev/sda1 /mnt

```

[INDENT]process of discovery --
one step at the time
[/INDENT]

---

### Post by MAFoElffen on 2023-06-09
+1 --
Verified from the Seagate Docs on their own drives and Ubuntu (to specify the type as exfat and use umask=000)

---

### Post by Hibari on 2023-06-10
> **Bashing-om said:**
> Hibari; Hello

Admittedly, I do not know a lot about Windows' file systems - however from my notes:
appears that one must also have  exfat-utils installed.

What happens when you explicitly tell the system to mount exfat ?
Like so:
```

sudo mount -t exfat -o umask=000 /dev/sda1 /mnt

```
[INDENT]process of discovery --
one step at the time
[/INDENT]



Unfortunately, neither option worked.

```
Reading package lists... DoneBuilding dependency tree... Done
Reading state information... Done
Package exfat-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'exfat-utils' has no installation candidate

```

```
sudo mount -t exfat -o umask=000 /dev/sda1 /mnt
mount: /mnt: unknown filesystem type 'exfat'.
```

---

### Post by Hibari on 2023-06-10
Update: mounting works fine on 5.15.71, but not on 72 or 73.

---

### Post by Hibari on 2023-06-10
Other update: upgrading to 5.19.16 solved this, although my graphic drivers died in the process.

---

### Post by TheFu on 2023-06-10
BTW, exFAT really shouldn't be used with HDDs or SSDs.  

It should only be used with USB Flash drives or microSD cards where keeping the write count low is very important.  

For SSD and HDD storage, **there are better file systems**.  For example, _NTFS_ would be better if retaining the ability to physically plug in the drive to an MS-Windows system is needed.  If access will only be over the network, then choose to format the partition(s) with a native Linux file system.  Samba network shares to MS-Windows will work and for native Linux/Unix systems NFS works best with Unix-file systems - say _ext4_.

Both NTFS and ext4 have journaling as part of the file system. This makes them safer to use and drastically reduces data lose and corruption.  In the 1990s, we didn't use file systems with journaling. I remember waiting 10+ hrs for an fsck to run.  With journaling, an fsck takes just a few minutes, at worst, plus we KNOW the data isn't corrupted due to file system issues.

---

