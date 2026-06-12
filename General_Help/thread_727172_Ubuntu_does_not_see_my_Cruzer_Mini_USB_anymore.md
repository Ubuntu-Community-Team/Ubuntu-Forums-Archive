---
title: "Ubuntu does not see my Cruzer Mini USB anymore"
date: 2008-03-17
forum: General Help
---

### Post by G_Stewart on 2008-03-17
I read the other posts and they weren't close enough to be of any help to me. I consider myself a mediocre Ubuntu user, not a newbie but not a guru either.
I recently upgraded to the newest version of Ubuntu (via update system) from the previous version. In the previous version it worked fine. After the upgrade, it doesn't come up when I insert the mini USB drive, nor can I find it anywhere to bring it up manually?

Gary

---

### Post by munkyeetr on 2008-03-17
Just on the off-chance of hardware failure, have you tested the Cruzer Mini on another machine to make sure it still works? (Just to cover the initial troubleshooting bases)

---

### Post by G_Stewart on 2008-03-17
LOL, yes. It works on my laptop running Mandrake.

---

### Post by munkyeetr on 2008-03-17
Okay, just checking. LOL

When you say you upgraded to the newest version, please clarify if you mean stable versions (7.04 - 7.10) or to the new beta (7.10 - 8.04).

---

### Post by munkyeetr on 2008-03-17
Also, please run the following commands from a Terminal window, make sure the CruzerMini is plugged into the machine:
```

blkid

```
and
```

cat /etc/fstab

```
and include them in your next post.

---

### Post by G_Stewart on 2008-03-17
Here's what I got with the first:

/dev/sda1: UUID="5874bf9c-eb75-4255-8d91-e4ab94714ed5" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="4f2e54d6-c42c-4be3-af68-9185e5c59975" TYPE="swap"
/dev/sdb1: UUID="2036ecc6-6277-11d9-951c-8a2ec938145b" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdc1: UUID="6832-56C7" TYPE="vfat"

And the 2nd:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5874bf9c-eb75-4255-8d91-e4ab94714ed5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4f2e54d6-c42c-4be3-af68-9185e5c59975 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /storage        ext3    defaults                0       0

And, lol, I'm not sure which version I got now. How do I find out, I'd like to know.

---

### Post by munkyeetr on 2008-03-17
You could try adding the device manually to your fstab file; open the file:
```

gksudo gedit /etc/fstab

```
add this line to the file:
```

/dev/sdc1 /media/usbdrive vfat defaults 0 0

```

then create the mount point:
```

sudo mkdir /media/usbdrive

```

then try mounting it:
```

sudo mount /media/usbdrive

```

---

### Post by munkyeetr on 2008-03-17
> **G_Stewart said:**
> And, lol, I'm not sure which version I got now. How do I find out, I'd like to know.

Enter this at the Terminal window:
```

cat /etc/issue

```

---

### Post by G_Stewart on 2008-03-17
Version 7.10 \n \l

Do I need to reboot or anything for it to take affect?

---

### Post by munkyeetr on 2008-03-17
You shouldn't. Did it not work?

---

### Post by G_Stewart on 2008-03-17
It doesn't seem to have worked. Nothing in my /mnt dir.

---

### Post by munkyeetr on 2008-03-17
It may not drop an icon on your desktop, you may need to go into the directory manually by opening Nautilus and navigating to /media/usbdrive
```

nautilus /media/usbdrive

```

---

### Post by munkyeetr on 2008-03-17
> **G_Stewart said:**
> It doesn't seem to have worked. Nothing in my /mnt dir.

Did you use /mnt or /media?

My example was /media (you can use either, but the mount point must be the same in both fstab and the mount command you put in at the Terminal.)

---

### Post by munkyeetr on 2008-03-17
Try reposting your modified fstab file, please.

---

### Post by G_Stewart on 2008-03-17
Ah. it is under /media LOL.But, I can't mount it. I tried to drop a file into it and it didn't work. All permissions are root only.

---

### Post by munkyeetr on 2008-03-17
First, unmount the drive:
```

sudo umount /media/usbdrive

```

Then, edit your fstab file again, making the following change to the entry you added (change is in bold):
```

/dev/sdc1 /media/usbdrive vfat defaults**,user** 0 0

```

This should allow users other than root to mount, unmount, and write to the disk...let me know.

Remount the drive:
```

mount /media/usbdrive

```

---

### Post by G_Stewart on 2008-03-17
OK, I found it, I can see what's on it but I still can't delete its contents. Everything is root permission. That was not the original permission.

Oh, yes. Thanks for all your help so far. I appreciate it.

Gary

How do I erase the mini?

---

### Post by munkyeetr on 2008-03-17
try:
```

cd /media
sudo chown -R <username> usbdrive

```

** substitute <username> with your username. This will give you permissions over the mount point and files.

---

### Post by G_Stewart on 2008-03-19
Thanks for the help. It is working fine.

Gary

---

### Post by munkyeetr on 2008-03-19
Is it auto-launching when you plug it in now also?

If it's not, I have no idea why. Perhaps someone else can help you get that going, but at least you got it so you can use it. Cheers. :)

---

### Post by G_Stewart on 2008-03-20
Well... I'm not sure. LOL. Once I found it and created a link to the desktop, when I plug in the Mini the icon changed to mounted. But, before I created the icon, it would not pop up on its own. I am happy now.

Thanks a lot again.

Gary :)

---

