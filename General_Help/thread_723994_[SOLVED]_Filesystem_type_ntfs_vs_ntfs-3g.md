---
title: "[SOLVED] Filesystem type: ntfs vs ntfs-3g"
date: 2008-03-14
forum: General Help
---

### Post by gobuntu on 2008-03-14
Dear friends,

On my Ubuntu 7.10, all updates current, some Windows XP partitions, clicking Properties show:

1. Filesystem type: ntfs

and another:

2. Filesystem type: ntfs-3g

Does anyone know WHY and what are the differences?

All partiions were made via Windows XP

Thanks!

---

### Post by TidusBlade on 2008-03-14
I dont think theres any difference...
If you installed ntfs-3g to write to NTFS partition it will probably say ntfs-3g but in the end, theyre both the same I guess.

---

### Post by gobuntu on 2008-03-14
> **TidusBlade said:**
> I dont think theres any difference...
If you installed ntfs-3g to write to NTFS partition it will probably say ntfs-3g but in the end, theyre both the same I guess.

Hi Tidus,

What do you mean, if, ntfs-3g IS ALREADY a part of Ubuntu Gutsy, according to this:
[COLOR="Sienna"]
NTFS writing

While previous Ubuntu releases only supported read access to Windows (NTFS) partitions, Gutsy Gibbon now fully supports reading and writing to them, by integrating the NTFS-3g project. This significantly eases file and document sharing with Windows.
[/COLOR]

However, I believe that there are some kinks on this issue, and am trying to find out the TRUTH, as NTFS read/write is very, very important here, and we are having some issues, that I will post separately in a little while.

Thanks!

---

### Post by TidusBlade on 2008-03-14
Oh ok then...
I forgot that it comes with Gutsy, but anyways, I never had much problems with ntfs-3g.
I would think it says ntfs-3g to show that it's being mounted using ntfs-3g maybe?

---

### Post by kpkeerthi on 2008-03-14
**NTFS:**
NTFS is a filesystem type like ext3. In the context of linux, it is both a filesystem and a 'driver' that has full read and partial write support to NTFS partitions. This driver has been obsoleted by ntfs-3g.

**NTFS-3G**
NTFS-3G is the latest linux 'driver' that provides full read and write support for NTFS partitions.

Hope that is clear.

---

### Post by gobuntu on 2008-03-14
> **kpkeerthi said:**
> **NTFS:**
NTFS is a filesystem type like ext3. In the context of linux, it is both a filesystem and a 'driver' that has full read and partial write support to NTFS partitions. This driver has been obsoleted by ntfs-3g.

**NTFS-3G**
NTFS-3G is the latest linux 'driver' that provides full read and write support for NTFS partitions.

Hope that is clear.

OK, friend,

But WHY, in the same pc, some partions show, as said initially, "ntfs", while another says "ntfs-3g" in Ubuntu?

The drives in Windows just say "NTFS"

If you are running Gutsy and have windows drives, what does Properties show for Filesystem of the NTFS?

Do they show ntfs-3g? Or just ntfs?

Thanks!

---

### Post by kpkeerthi on 2008-03-14
Can you post the content of /etc/fstab?
```
cat /etc/fstab
```

---

### Post by vikrant82 on 2008-03-14
```
kx@Kx-VMZ:/$ ls /sbin/mount* -l
-rwsr-xr-x 1 root root 23340 2008-03-13 18:41 /sbin/mount.cifs
-rwxr-xr-x 1 root root  5732 2008-02-26 23:55 /sbin/mount.fuse
lrwxrwxrwx 1 root root    12 2008-03-07 22:42 /sbin/mount.ntfs -> /bin/ntfs-3g
lrwxrwxrwx 1 root root    12 2008-03-07 22:42 /sbin/mount.ntfs-3g -> /bin/ntfs-3g
lrwxrwxrwx 1 root root    18 2008-02-24 19:11 /sbin/mount.ntfs-fuse -> /usr/bin/ntfsmount
-rwxr-xr-x 1 root root  2538 2008-03-13 18:40 /sbin/mount.smbfs
```

So if you see, mount.ntfs is just a link to ntfs-3g, So, They are one and the same thing.

---

### Post by gobuntu on 2008-03-14
> **kpkeerthi said:**
> Can you post the content of /etc/fstab?
```
cat /etc/fstab
```

Hi kpkeerthi,

The cat shows ntfs-3g for the internal drives which at the desktop icon show Filesystem: ntfs.

The usb drive, which at the icon shows Properties: ntfs-3g, does not show at the fstab.

Now I moved the usb drive to another laptop, and there, on the desktop icon, the same usb-drive DOES NOT show ntfs-3g, simply ntfs!

I had never seen Filesystem "ntfs-3g" when clicking at the drive icon at the desktop.

T'hat's why I noticed this and am asking, if anyone knows why.

Thanks.

---

### Post by gobuntu on 2008-03-14
> **vikrant82 said:**
> ```
kx@Kx-VMZ:/$ ls /sbin/mount* -l
-rwsr-xr-x 1 root root 23340 2008-03-13 18:41 /sbin/mount.cifs
-rwxr-xr-x 1 root root  5732 2008-02-26 23:55 /sbin/mount.fuse
lrwxrwxrwx 1 root root    12 2008-03-07 22:42 /sbin/mount.ntfs -> /bin/ntfs-3g
lrwxrwxrwx 1 root root    12 2008-03-07 22:42 /sbin/mount.ntfs-3g -> /bin/ntfs-3g
lrwxrwxrwx 1 root root    18 2008-02-24 19:11 /sbin/mount.ntfs-fuse -> /usr/bin/ntfsmount
-rwxr-xr-x 1 root root  2538 2008-03-13 18:40 /sbin/mount.smbfs
```

So if you see, mount.ntfs is just a link to ntfs-3g, So, They are one and the same thing.

I agree that there's only ntfs-3g running in my system because I can read and write ntfs, and because that's what was implemented in Gutsy, but don't know why at my desktop icon, when I click on drive properties I get Filesystem: ntfs-3g which I had never seen that, just Filesystem: ntfs

Thanks

---

### Post by kpkeerthi on 2008-03-14
Looks like a (minor) bug in HAL (as it appears only on your automounted USB disk). ntfs-3g is not a filesystem.

---

### Post by gobuntu on 2008-03-14
Yes, Filesystem NTFS 3.1 is what I have.

Can't attribute any problem to this. Will report back after some more checking.

Thanks.

---

### Post by gobuntu on 2008-03-15
SOLVED:

See this thread:
[http://ubuntuforums.org/showthread.php?t=724011](http://ubuntuforums.org/showthread.php?t=724011)

---

