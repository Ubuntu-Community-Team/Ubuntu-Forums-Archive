---
title: "Unable to mount OS"
date: 2013-02-17
forum: General Help
---

### Post by jimbaggy on 2013-02-17
When I try to access my windows 8 files on ubuntu, it gives me this error 

```
Error mounting /dev/sda3 at /media/jim/OS: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda3" "/media/jim/OS"' exited with non-zero exit status 14: Hibernated non-system partition, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g -o remove_hiberfile /dev/sda3 /media/jim/OS

```

When I type in the command line ```

            mount -t ntfs-3g -o remove_hiberfile /dev/sda3 /media/jim/OS
``` in terminal, it says that > mount: only root can do that
I can't boot to windows 8 right now, it just loops a "preparing automatic repair loop" no matter what I do, even when I enable safemode, it still goes to that screen first and I'm unable to do anything. 

Can anyone help me?

---

### Post by diesch on 2013-02-17
You need root privileges to mount a file system. Try

```
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda3 /media/jim/OS
```

---

### Post by jimbaggy on 2013-02-17
> **diesch said:**
> You need root privileges to mount a file system. Try

```
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda3 /media/jim/OS
```

Just tried that but got this 
```
fuse: failed to access mountpoint /media/jim/OS: No such file or directory

```

---

### Post by diesch on 2013-02-17
The folder* /media/jim/OS* doesn't exist. Use
```
sudo mkdir -p /media/jim/OS
```to create it.

---

### Post by jimbaggy on 2013-02-17
> **diesch said:**
> The folder* /media/jim/OS* doesn't exist. Use
```
sudo mkdir -p /media/jim/OS
```to create it.

It works, but now I get this: 
```
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

```

---

### Post by Mark Phelps on 2013-02-17
You can't mount as Hibernated partition -- and even if you could, any changes you made to it would be erased when you went back into Windows, and quite possibly, that would corrupt the partition filesystem as well.

If you're going to dual-boot, you need to turn off hibernation in Windows -- to be safe.

---

