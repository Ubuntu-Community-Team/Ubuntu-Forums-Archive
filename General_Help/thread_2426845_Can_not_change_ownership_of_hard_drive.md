---
title: "Can not change ownership of hard drive"
date: 2019-09-14
forum: General Help
---

### Post by Jonners59 on 2019-09-14
I am using a seperate hard drive for all my document storage.  As I have a dual boot Windows to allow me to use the odd program that will only work on Windows it is formatted to NTFS.  It mounts, using fstab as follows...
```
#Entry for /dev/sda3 :
UUID=XXXXXXXXXXX	/media/Documents	ntfs-3g	defaults,rw, uid=1000,locale=en_GB.UTF-8	0	0
```

The Directory and all its contents are opening as root.  This is a problem because it means anything I store there is also owned by root and can mean that some days nothing works, i.e.  I can't copy, delete or even store things in these folders.  I say sometimes, because sometimes, it seems to allow me, but mostly I have little control.

I have tried opening Nautilus as root and changing permissions and ownership but it reverts back.

How can I fix this, please?

---

### Post by coffeecat on 2019-09-14
You are showing a space between two of your mount options in your fstab line, thus:

```
defaults,rw, uid=1000,locale=en_GB.UTF-8
```

Assuming that wasn't a transcription error in your post, remove the space so that the options read:

```
defaults,rw,uid=1000,locale=en_GB.UTF-8
```

Unmount and remount the partition and see if that fixes it. If not, hopefully someone with more knowledge of mounting ntfs filesystems will be along to help.

---

### Post by Jonners59 on 2019-09-18
> **coffeecat said:**
> You are showing a space between two of your mount options in your fstab line, thus:

```
defaults,rw, uid=1000,locale=en_GB.UTF-8
```

Assuming that wasn't a transcription error in your post, remove the space so that the options read:

```
defaults,rw,uid=1000,locale=en_GB.UTF-8
```

Unmount and remount the partition and see if that fixes it. If not, hopefully someone with more knowledge of mounting ntfs filesystems will be along to help.

Thank you.
will give it a go.  just changed fstab, will see what happens next reboot.  My concern is that Windows MIGHT be locking it....

---

### Post by TheFu on 2019-09-18
Then tell Windows to properly close the file system always at shutdown.

Changing permissions doesn't work on NTFS file systems under Linux. The permissions are set at mount time for all the files and directories. There are mount options to control them, but they are for all files and all directories.  Using a Linux file system is better for that reason, but also because Linux file systems like ext4 use kernel drivers, so they aren't so slow, like NTFS.

I use these options when mounting NTFS for use by my main userid (1000:1000):
```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000
```
Some are for security, some for performance, some to force filenames that Windows will like.

---

### Post by Jonners59 on 2019-09-26
Sorry, not had any notifications.  I agree about file type.  I'll give your mount options a go and see what happens - fingers crossed.

---

### Post by Jonners59 on 2019-09-29
> **TheFu said:**
> Then tell Windows to properly close the file system always at shutdown.

Changing permissions doesn't work on NTFS file systems under Linux. The permissions are set at mount time for all the files and directories. There are mount options to control them, but they are for all files and all directories.  Using a Linux file system is better for that reason, but also because Linux file systems like ext4 use kernel drivers, so they aren't so slow, like NTFS.

I use these options when mounting NTFS for use by my main userid (1000:1000):
```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000
```
Some are for security, some for performance, some to force filenames that Windows will like.


You know what, I think that has fixed it.  Thank you.
```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000
```

from
```
[COLOR=#000000][FONT=&quot]defaults,rw,uid=1000,locale=en_GB.UTF-8[/FONT][/COLOR]
```

Thank you.

:-)

---

