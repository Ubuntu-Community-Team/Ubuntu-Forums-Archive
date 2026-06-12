---
title: "chmod -R fails on mounted drive"
date: 2014-02-16
forum: General Help
---

### Post by IanVaughan on 2014-02-16
I have a mounted drive that is 777, and I can't change it, damn annoying!

```

ian@bart:/mnt$ ls -asl
total 40
 4 drwxr-xr-x  5 root root  4096 Jan 29 20:06 .
 4 drwxr-xr-x 23 root root  4096 Jan 21 21:39 ..
24 drwxrwxrwx  1 root root 24576 Feb  2 19:41 data

```

I've tried with and without "sudo" :
```

chmod -R 664 /mnt/data/

```

but nothing changes!

Here is the mount : 

```

ian@bart:/mnt$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=e1b625c7-32c7-41b0-96fe-1608805d7094 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=1115979a-9ad2-439b-b40f-8405d65f7070 none            swap    sw              0       0

https://www.box.com/dav /home/ian/Box         davfs rw,user,noauto 0 0
/dev/disk/by-uuid/1C7A67D17F77AEE4 /mnt/data auto nosuid,nodev,nofail,x-gvfs-show 0 0

```

---

### Post by sandyd on 2014-02-16
Is that a NTFS drive by any chance - NTFS doesn't support linux permissions by default, unless you add the permissions option
i.e.
```

/dev/disk/by-uuid/1C7A67D17F77AEE4 /mnt/data auto nosuid,nodev,nofail,x-gvfs-show,permissions 0 0
```

---

### Post by IanVaughan on 2014-02-16
Damn, it is, if I remember correctly (it was setup a while back!).
Ok, so its due a reformat... 
Cheers!

---

### Post by Morbius1 on 2014-02-16
> /dev/disk/by-uuid/1C7A67D17F77AEE4 /mnt/data auto nosuid,nodev,nofail,x-gvfs-show 0 0
Because 1C7A67D17F77AEE4 is the uuid of an ntfs partition any you can't change it with a chmod.

Change your fstab entry to this if you want 775 ( you really don't want 664 - you wouldn't be able to open any folders ):
> /dev/disk/by-uuid/1C7A67D17F77AEE4 /mnt/data auto nosuid,nodev,nofail,x-gvfs-show,[COLOR=#0000cd]**umask=002**[/COLOR] 0 0

After you make the change unmount the partition:
```
sudo umount /mnt/data
```
And remount t with this:
```
sudo mount -a
```

[COLOR=#0000cd]**EDIT**: If this is a dual boot with windows you don't want to add the "permissions" option or you will end up in a world of hurt.[/COLOR]

---

### Post by IanVaughan on 2014-02-16
OH wow, many thanks.
That worked a treat.

Extra thanks for highlighting the change required, appreciated.

(And oh yeah, 775 sounds good!)

---

