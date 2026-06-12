---
title: "Writing to mounted truecrypt volume"
date: 2007-08-15
forum: General Help
---

### Post by keymoo on 2007-08-15
Hi,

I have a truecrypt volume on my CORSAIR USB device and want to mount it at ~/tc and then modify its contents.

I tried the following command

```
sudo truecrypt --mount-options "rw,sync,utf8,uid=1000,umask=0000" /media/CORSAIR tc
```

in [this thread]("http://ubuntuforums.org/showthread.php?t=442259") and I can view the files but cannot change them. Does anyone know what command I should issue?

Thanks,
keymoo

---

### Post by OoooMatron on 2007-08-15
You don't say what file format you are using but this command gives me read/write ntfs.

sudo truecrypt /media/sdd5/media /media/tc1 --filesystem ntfs-3g -M "rw,gid=users,umask=0000"

first path is the container location and the second path is the mount location. Think you can drop the umask and make sure there are no spaces in the "" after -M

---

### Post by keymoo on 2007-08-16
Thanks for the reply.

I can't remember what file system I formatted it as now. How do I find out? Is there a command to issue to discover the file system a volume is using? I tried df -h, but it didn't show it.

Thanks

---

### Post by keymoo on 2007-08-16
I plugged the USB device into a Windows machine to see what filesystem it was and its FAT32. How do I modify the command so it uses FAT32? Thanks

---

### Post by keymoo on 2007-08-16
Well, I've tried every combination of options I could think of including:

```
--filesystem vfat
--filesystem ntfs-3g
```

Still no joy, the volume mounts as read only. Please help, thanks.

---

### Post by keymoo on 2007-09-12
This problem still remains unsolved - if anyone knows **please **reply, thanks.

---

### Post by skralljt on 2008-04-08
Have you tried  the chown command?  type man chown on the command prompt to learn about it.

---

