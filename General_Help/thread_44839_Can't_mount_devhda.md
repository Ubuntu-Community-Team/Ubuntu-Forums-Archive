---
title: "Can't mount /dev/hda"
date: 2005-06-27
forum: General Help
---

### Post by beeldings on 2005-06-27
I have been trying to mount my hard drive, /dev/hda, because I made a few changes to my /etc/fstab file and I cannot boot Ubuntu from my hard drive. The change I made was the addition of "noatail" to /dev/hda1, the main partition of the hard drive (where Ubuntu is installed), and now most of the services fail at start-up and the system freezes at "Starting System Log..."

Anyway, I loaded the Live CD and tried to mount /dev/hda1 in a terminal so I could remove the "noatail" option from my fstab file. However, when I try to mount the drive:

```

mount: can't find /dev/hda in /etc/fstab or /etc/mtab

```

I tried mounting the drive both as the super user (sudo mount /dev/hda1) and as root (sudo su - | mount /dev/hda1) and nothing worked. So, what I can I do in order to mount /dev/hda1 so I can edit the fstab file?

---

### Post by dialate on 2005-06-27
You need to specify what directory to mount it to. If you don't, mount assumes you mean something in fstab or mtab.

Also, you need to specify which partition. hda is just a hard disk. You need hda1 or hda2 or something.

So, you would first create a directory to mount to - sudo mkdir /mount/foo
Then - sudo mount /dev/hda1 /mount/foo

---

### Post by Xian on 2005-06-27
I'm not familiar with Ubuntu's LiveCD but it seems unusual that it (a LiveCD) would not automount your partitions. The problem most people have is wondering how to gain write access to them since distros like Knoppix usually mount them as ro. If you issue the mount command does it not list your /hda1?
```
$ mount
```
If not then you should probably just try mounting it to a specific directory on the LiveCD. That is what your error message is complaining about. You are telling it to mount a partition that is not preconfigured in the fstab file and therefore has no attributable directory. This can be done manually in the mount command by simply providing the path.

---

### Post by mingus on 2005-06-28
The Live-CD does not automount anything.  It creates a RAM image to work inside.  I have found that the mount command sometimes must be explicit, e.g., include the filesystem type.  When I use it, I do what :rescue does from the install CD, I mount the / partition to /target (and then any other partitions, like for /boot).  And then I chroot to /target.

---

