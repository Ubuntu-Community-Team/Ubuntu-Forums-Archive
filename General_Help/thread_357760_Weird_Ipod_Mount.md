---
title: "Weird Ipod Mount"
date: 2007-02-10
forum: General Help
---

### Post by Inhumane on 2007-02-10
For some reason I can't figure out the path that my Ipod is being mounted to. It isn't in /mnt, nor is it in /media. It does show up in Computer under the name "Apple Ipod Music Player" but is unaccessible and the location says "computer:///". I am also unable to get it to work with Gtkpod. Anything I could try to fix it?

---

### Post by gradedcheese on 2007-02-10
You can run "mount" in a terminal to see all mounted file systems and their mount point.  Does it show up in that list?  Oh, also: which iPod?  I have the 2nd generation Nano and it has an interesting bug (shows up as a RAID device!) that requires a simple patch to HAL that some nice person did in order to work (after that, it works beautifully).

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> You can run "mount" in a terminal to see all mounted file systems and their mount point.  Does it show up in that list?  Oh, also: which iPod?  I have the 2nd generation Nano and it has an interesting bug (shows up as a RAID device!) that requires a simple patch to HAL that some nice person did in order to work (after that, it works beautifully).

Doesn't look like it shows up on mount:
```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```
But ls -l /dev/disk/by-id/usb* shows
```
lrwxrwxrwx 1 root root  9 2007-02-10 01:25 /dev/disk/by-id/usb-Apple_iPod_000A270014CC12A3 -> ../../sdb
lrwxrwxrwx 1 root root 10 2007-02-10 01:25 /dev/disk/by-id/usb-Apple_iPod_000A270014CC12A3-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-02-10 01:25 /dev/disk/by-id/usb-Apple_iPod_000A270014CC12A3-part2 -> ../../sdb2

```

Oh, and my iPod is 5th gen

---

### Post by gradedcheese on 2007-02-10
weird!  ok, so we know your iPod is /dev/sdb1 at least.  I wonder if Nautilus just uses the sysfs info without seeing if it got mounted.  Perhaps try manually mounting it:

sudo mkdir /mnt/ipod
sudo mount -t vfat /dev/sdb1 /mnt/ipod

ls /mnt/ipod
(does it look like a valid iPod file system?)

...then run "sudo gtkpod" and tell it to look in /mnt/ipod  ...if that works, you can either add it to fstab (with 'user' permissions, there are guides about this) or (again after reading some iPod guides), edit the udev/hal filters so that the product name (via sysfs as you posted) gets recognized correctly.  I've seen some nice info about this but I can't remember where.

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> weird!  ok, so we know your iPod is /dev/sdb1 at least.  I wonder if Nautilus just uses the sysfs info without seeing if it got mounted.  Perhaps try manually mounting it:

sudo mkdir /mnt/ipod
sudo mount -t vfat /dev/sdb1 /mnt/ipod

ls /mnt/ipod
(does it look like a valid iPod file system?)

...then run "sudo gtkpod" and tell it to look in /mnt/ipod  ...if that works, you can either add it to fstab (with 'user' permissions, there are guides about this) or (again after reading some iPod guides), edit the udev/hal filters so that the product name (via sysfs as you posted) gets recognized correctly.  I've seen some nice info about this but I can't remember where.
sudo mount -t vfat /dev/sdb1 /mnt/ipod:
```
mount: unknown filesystem type 'vfat'
```
"ls /mnt/ipod"
shows nothing
:(

---

### Post by gradedcheese on 2007-02-10
> 
mount: unknown filesystem type 'vfat'


well, I bet this had to do with your problem!  If you don't have VFAT (ie: FAT16 and FAT32 file system) support, then there's no way to mount an iPod (which will be in FAT format if it's a "Windows-formatted" iPod).  Now what is weird is that vfat support should have been provided, I've never seen it not be provided in a desktop distribution.  Are you running a custom kernel or something?

In /boot/ there are files that start with "config-2.6.", those are your kernel configs.  Run "uname -r" to get your kernel name, and then look at the appropriate /boot/config file... go to where it says "# DOS/FAT/NT Filesystems" and make sure you have "CONFIG_FAT_FS=m" and "CONFIG_VFAT_FS=m" rather than it being commented out.  If it is commented out, then you have the problem of not having vfat support...

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> well, I bet this had to do with your problem!  If you don't have VFAT (ie: FAT16 and FAT32 file system) support, then there's no way to mount an iPod (which will be in FAT format if it's a "Windows-formatted" iPod).  Now what is weird is that vfat support should have been provided, I've never seen it not be provided in a desktop distribution.  Are you running a custom kernel or something?

Yup, and I was thinking that that was the problem as well, but wasn't too sure. I compiled a custom kernel just today. I'm still new at it, but would you say it's possible to simply update a kernel without having to go through the whole recompile process again?

Also, would it be possible to format the iPod for "mac" systems so that it no longer uses Windows and I'll be able to mount it?

---

### Post by gradedcheese on 2007-02-10
For the 'mac' version, you'd need HFS or HFS+ file system support, do you have that? ;)

If you didn't enable VFAT when you menuconfig'ed your custom kernel, then I'm afraid you'll need to recompile.  While you're at it, look at the options really carefully because you might have missed something else.

Here's the "safe" way to configure custom kernels:

1) start with your old config!  Say the last off-the-shelf kernel you used is "2.6.17-10-386", and you are in the kernel build directory:
sudo cp /boot/config-2.6.17-10-386 .config
(ie: copy my Ubuntu kernel config as the new config)
2) now configure based on that:
make menuconfig

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> For the 'mac' version, you'd need HFS or HFS+ file system support, do you have that? ;)

If you didn't enable VFAT when you menuconfig'ed your custom kernel, then I'm afraid you'll need to recompile.  While you're at it, look at the options really carefully because you might have missed something else.

Here's the "safe" way to configure custom kernels:

1) start with your old config!  Say the last off-the-shelf kernel you used is "2.6.17-10-386", and you are in the kernel build directory:
sudo cp /boot/config-2.6.17-10-386 .config
(ie: copy my Ubuntu kernel config as the new config)
2) now configure based on that:
make menuconfig

I don't have those either :( I did look carefuly at the choices, I just thought I wouldn't need anything Windows related anymore :lolflag: Oh well, I'll just wait until a new kernel comes out or fiesty, whichever comes first. I've already had a 30 or so hour trip to the recompile factory in the past couple of days (SATA options)

Thanks a bunch for the help!

---

### Post by gradedcheese on 2007-02-10
You're welcome.  Incidentally, FAT support is very important and really (in modern times) has little to do with Windows.  It's a cheap and easy file system to implement, so you'll find it **everywhere** -- SD cards, digital cameras, music players, etc etc.  Chances are you'll need it no matter what.

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> weird!  ok, so we know your iPod is /dev/sdb1 at least.  I wonder if Nautilus just uses the sysfs info without seeing if it got mounted.  Perhaps try manually mounting it:

sudo mkdir /mnt/ipod
sudo mount -t vfat /dev/sdb1 /mnt/ipod

ls /mnt/ipod
(does it look like a valid iPod file system?)

...then run "sudo gtkpod" and tell it to look in /mnt/ipod  ...if that works, you can either add it to fstab (with 'user' permissions, there are guides about this) or (again after reading some iPod guides), edit the udev/hal filters so that the product name (via sysfs as you posted) gets recognized correctly.  I've seen some nice info about this but I can't remember where.

OK, sorry for the bump, but I have just recompiled my Kernel and included the VFAT file system.
When I do sudo mount -t vfat /dev/sdb1 /mnt/ipod, this is what shows up ```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
dmseg | tail shows this ```
SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
sdb: Write Protect is off
sdb: Mode Sense: 68 00 00 08
sdb: assuming drive cache: write through
 sdb: sdb1 sdb2
sd 2:0:0:0: Attached scsi removable disk sdb
sd 2:0:0:0: Attached scsi generic sg1 type 0
usb-storage: device scan complete
FAT: invalid media value (0x2f)
VFS: Can't find a valid FAT filesystem on dev sdb1.

```

---

### Post by gradedcheese on 2007-02-10
Hmm... maybe it's actually /dev/sdb2 that you want (one is the iPod OS partition, the other is the FAT where the music is stored)

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> Hmm... maybe it's actually /dev/sdb2 that you want (one is the iPod OS partition, the other is the FAT where the music is stored)

Same messege

---

### Post by gradedcheese on 2007-02-10
weird.  Is the iPod file system perhaps corrupt?  Can you plug it in to a Windows PC (something with iTunes) and verify that it's working?

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> weird.  Is the iPod file system perhaps corrupt?  Can you plug it in to a Windows PC (something with iTunes) and verify that it's working?

I don't have another PC around, but the Ipod itself plays music just fine, and it worked in Windows a week ago before I moved to Ubuntu again

---

### Post by gradedcheese on 2007-02-10
Oh, ok.  Can you verify that it still comes up as /dev/sdb by looking at /dev/disk/by-id again?  (or look at dmesg)  Also, now that you have FAT support, check that it's not automatically mounted somewhere.

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> Oh, ok.  Can you verify that it still comes up as /dev/sdb by looking at /dev/disk/by-id again?  (or look at dmesg)  Also, now that you have FAT support, check that it's not automatically mounted somewhere.

```
usb-Apple_iPod_000A270014CC12A3
usb-Apple_iPod_000A270014CC12A3-part1
usb-Apple_iPod_000A270014CC12A3-part2

```
It's not mounted, I cannot access it through Computer, and it's not on the desktop and not in /mnt


Could I be missing some other filesystems that are needed to use an iPod that you could think of?

---

### Post by gradedcheese on 2007-02-10
right, but where does that stuff point?

ls -al /dev/disk/by-id/

---

### Post by Inhumane on 2007-02-10
!!!! I logged in as a different user and the ipod mounts wonderfuly! So it's a permission issue. I cannot think why, though. I am under the root user group (tried admin as well) and I have full user privileges. :confused: This also explains why I couldn't mount a CD :)

---

### Post by gradedcheese on 2007-02-10
Ah!  Double-check that the contents of /etc/group make sense

---

### Post by Inhumane on 2007-02-10
> **gradedcheese said:**
> Ah!  Double-check that the contents of /etc/group make sense

Umm, I can't really tell what they all mean, what do I set there to make myself almost as powerful as root?

---

### Post by gradedcheese on 2007-02-10
You could do this:

/etc/group | grep your_user_name

to see which groups you belong to (the group name is on the very left of each line).  I think that you should be in 'admin', 'adm', 'cdrom', and a few others.  Also there should be a group like this:

```

your_user_name:x:1000:

```
Basically, just verify that things there look reasonable.  perhaps compare them to the other user's (the one that can mount the iPod just fine) memberships and see where they differ.

---

