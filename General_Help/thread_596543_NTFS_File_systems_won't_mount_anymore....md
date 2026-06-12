---
title: "NTFS File systems won't mount anymore..."
date: 2007-10-29
forum: General Help
---

### Post by ownaginatious on 2007-10-29
I recently installed Ubuntu 7.10 and was annoyed to find out that my drives aren't mounting.. I managed to fix by forcefully unmounting them and then remounting, which worked (I had just installed ubuntu over my windows system disk to access the two storage disks). So I set it up in the fstab to automount at startup, and it seemed to work. Now all of a sudden after restarting, both my NTFS storage drives tell me "Cannot mount volume, You are not privilaged to mount the volume 'Server Backup'.

This is REALLY pissing me off... I really want to like Linux, but everything that was a no-brainer in windows is a whole console-based adventure in linux...

Besides my rant, can anyone help? I really want to get these drives working so that I can use SMB (I need to back stuff up to the drives from other computers soon). Thanks!

Here is the fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8dd00287-d572-4f43-8f2a-2b3480e12ccc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7cc8109d-c6b1-4145-b0b3-8ff2451b069e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/hdc1 /media/windows ntfs nls=utf8,umask=0222 0 0
```

---

### Post by taurus on 2007-10-29
How come you mount two different partitions to the same mount point in /etc/fstab?

> **/dev/hdb1 /media/windows** ntfs nls=utf8,umask=0222 0 0
**/dev/hdc1 /media/windows** ntfs nls=utf8,umask=0222 0 0
What happens if you try to mount it from a terminal to see exactly what's wrong with it?

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs /dev/hdb1 /media/windows
```

---

### Post by ownaginatious on 2007-10-29
```
fuse: failed to access mountpoint /media/windows: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 (Server Drive)

```

That's the error I get... and with regards to that same mounting point thing I had, how am I supposed to do it? I read a tutorial to do that, but it was pretty vague, so that's probably why I messed up. :p

---

### Post by taurus on 2007-10-29
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and change the last two lines to look like these.

```

/dev/hdb1  /media/windows1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdc1  /media/windows2   ntfs   nls=utf8,umask=0222   0   0

```
Save it.  Then, create those two new mount points and mount them.

```
sudo mkdir /media/windows1 /media/windows2
sudo mount -a
df -h
```

---

### Post by ownaginatious on 2007-10-29
Wow, that worked! Thanks a lot :)

---

### Post by ownaginatious on 2007-10-30
Ok, it looks like I spoke too soon. Both my drives will mount, as stated before, but I cannot write to either of them and it says:

"/directory/file.txt" cannot be deleted because you do not have permissions to modify its parent folder.

I think the problem is that it is set to read only under the root... and I'm a pretty big noob to linux, and don't know how to set the permissions to how I want. Could someone please help me sort this out?

And on a side not, both my drives happen to have spaces in the naming (i.e. /Server Drive/Server Core Folder), does anyone know how I enter these in the terminal when wanting to change things? I tried replacing the spaces with underscores, but it didn't seem to work very well...

---

