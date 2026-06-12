---
title: "Need a Little Help with Mounting"
date: 2007-09-07
forum: General Help
---

### Post by xluryan on 2007-09-07
Hey there, just a quick question here (hopefully...).

I have an externall HDD. There are 2 partitions on it. One is an ext3, and the other is a fat32.

For some reason, when my computer starts up, the fat32 partition is owned by me in my group. But the ext3 partition is root:root.

Any ideas?

---

### Post by merlinus on 2007-09-07
You can change this via chown or chmod.

What is the partition and mountpoint?

-merlin

---

### Post by xluryan on 2007-09-08
Yeah, I've already tried everything I can think of. Here is some output for you to check out:

"disk" is the ext3, and "disk-1" is the fat32.

```

ryan@freedom:/media$ ls -l
total 68
lrwxrwxrwx  1 root root        6 2007-05-05 14:06 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2007-05-05 14:06 cdrom0
drwxr-xr-x  2 root root     4096 2007-05-05 14:06 cdrom1
drwxr-xr-x 11 root root    32768 1969-12-31 17:00 disk
drwxr-xr-x  2 ryan root     4096 2007-09-07 21:22 disk-1
dr-xr-x---  1 root plugdev 20480 2007-09-03 20:48 sda1
drwxr-xr-x  2 root root     4096 2007-05-19 19:06 sdc
ryan@freedom:/media$ sudo chown ryan:ryan disk
chown: changing ownership of `disk': Operation not permitted
ryan@freedom:/media$ sudo chmod 777 disk
ryan@freedom:/media$ ls -l
total 68
lrwxrwxrwx  1 root root        6 2007-05-05 14:06 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2007-05-05 14:06 cdrom0
drwxr-xr-x  2 root root     4096 2007-05-05 14:06 cdrom1
drwxr-xr-x 11 root root    32768 1969-12-31 17:00 disk
drwxr-xr-x  2 ryan root     4096 2007-09-07 21:22 disk-1
dr-xr-x---  1 root plugdev 20480 2007-09-03 20:48 sda1
drwxr-xr-x  2 root root     4096 2007-05-19 19:06 sdc
ryan@freedom:/media$

```

Weird, eh?

---

### Post by merlinus on 2007-09-08
Try this:

```

sudo chmod -R a+rwX /media/disk

```-merlin

---

