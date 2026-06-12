---
title: "Removing Windows from dual boot"
date: 2008-06-03
forum: General Help
---

### Post by webcoded612 on 2008-06-03
Here's the scenario:

I had Windows XP installed on the hard drive.  I used the Ubuntu installer to resize the partition to make room for Ubuntu.  I must've misread, because I meant to give Ubuntu 50Gb and leave the rest to Windows.  Instead, it gave Windows 50Gb and left the rest to Ubuntu.  

When I booted into Windows it started bugging out.  I don't know if this is from the partition or if it's just because it's Windows.  Anyway, I want to get rid of Windows altogether and just run Ubuntu.  How do I do this?

I can log into the Windows partition from Ubuntu and access all the files.  I thought of just deleting everything there, but I don't know how that will affect GRUB or Ubuntu itself.  Resizing the partition again is not an option without a total format:  Live CD doesn't work for me and Gparted's Live CD doesn't recognize my video card.  

Any ideas?  Thanks!

---

### Post by leito666 on 2008-06-03
If you want to remove it from grub you can do:

sudo gedit /boot/grub/menu.lst

scroll down, and remove the lines that involves windows.

---

### Post by webcoded612 on 2008-06-03
> **leito666 said:**
> If you want to remove it from grub you can do:

sudo gedit /boot/grub/menu.lst

scroll down, and remove the lines that involves windows.

Right but will it mess with the boot up?  Since Linux is installed on the second partition (I'm assuming), will there be any problems with boot?

I just don't want to break anything here....  :)

Thanks!

---

### Post by logos34 on 2008-06-03
> **webcoded612 said:**
> Right but will it mess with the boot up?  Since Linux is installed on the second partition (I'm assuming), will there be any problems with boot?

If it's listed in fstab and you were to format it, then yes it would throw and error at boot looking for it/ntfs partition to automount

post output for:

sudo fdisk -l

cat /etc/fstab

---

### Post by webcoded612 on 2008-06-03
> **logos34 said:**
> If it's listed in fstab and you were to format it, then yes it would throw and error at boot looking for it/ntfs partition to automount

post output for:

sudo fdisk -l

cat /etc/fstab

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc6ba95f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6091    48925926    7  HPFS/NTFS
/dev/sda2            6092        9729    29222235    5  Extended
/dev/sda5            6092        9573    27969133+  83  Linux
/dev/sda6            9574        9729     1253038+  82  Linux swap / Solaris

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000e990

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       19457   156288321    7  HPFS/NTFS

```

AND:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8605c19c-8025-4548-b8d1-c08bcc40ce7a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f0eec680-4989-4a0e-bb76-0a504f2ce86a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by Xiong Chiamiov on 2008-06-03
Since there's a good chance that you'll be breaking GRUB sometime soon in the future, it'd be a good idea to burn a copy of [SuperGrubDisk]("http://supergrubdisk.org").  It's amazing.

---

### Post by webcoded612 on 2008-06-03
I'm starting to wonder if it wouldn't just be easier to reformat the whole drive.  I don't care about losing Window$ - I want it gone.  Reformatting with the alternate disc takes about an hour, which is nothing compared to how long I could spend fixing what I break trying to get all this mess straightened up.  

I dunno.  Can this be fixed easily?  Or would a reformat/reinstall of Ubuntu using the whole partition be easier?

---

### Post by logos34 on 2008-06-03
It's not listed in fstab, so you can just unmount sda1, delete it, and then format it ext3 with gparted:

system>admin>partition editor

add it to fstab so it automounts

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

ADD: doesn't take but a couple if minutes.  Ont he other hand, if you want the grow the extended/sda2 to the front of the disk to take up the freed space after deleting windows, then you'd have to do that from the CD (root cannot be mounted) and that DOES take quite a while (resizing the left border, that is)

---

### Post by webcoded612 on 2008-06-03
> **logos34 said:**
> It's not listed in fstab, so you can just unmount sda1, delete it, and then format it ext3 with gparted:

system>admin>partition editor

add it to fstab so it automounts

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

ADD: doesn't take but a couple if minutes.  Ont he other hand, if you want the grow the extended/sda2 to the front of the disk to take up the freed space after deleting windows, then you'd have to do that from the CD (root cannot be mounted) and that DOES take quite a while (resizing the left border, that is)

Isn't that what the /dev/sda1 is?  It says NTFS on the right, and has the * to make it boot, as well.  

I know little and less about fstab, just wanted to make sure you didn't overlook somethin.  

Hell, I'll probably just format the whole thing.  Simpler that way.  

Thanks for the help!

---

### Post by webcoded612 on 2008-06-03
Ok so I figured this out.  Linux isn't stable enough to tinker with if you don't know what you're doing (and I don't), so I went the wipe-the-whole-system-and-start-over route.  

Thanks all for the help.  :)

---

### Post by logos34 on 2008-06-03
> **webcoded612 said:**
> Ok so I figured this out.  Linux isn't stable enough to tinker with if you don't know what you're doing (and I don't), so I went the wipe-the-whole-system-and-start-over route.  

Thanks all for the help.  :)

ok, whatever makes you happy

but all you needed to do as far as I can tell is delete sda1 ntfs (windows) partition, create a new primary ext3 partition in its place, and add a line to fstab. Grub/boot wouldn't have been affected

---

