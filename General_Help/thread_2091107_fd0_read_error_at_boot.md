---
title: "fd0 read error at boot"
date: 2012-12-04
forum: General Help
---

### Post by satimis on 2012-12-04
Hi all,

Ubuntu 12.04 desktop 64bit

Newly installed.

At boot a warning "Error: fd0 read error" popup.

Dectect floppy alread disabled at BIOS.  Google search said it is a bug.  Please advise is there any solution?  TIA

B.R.
satimis

---

### Post by oldfred on 2012-12-04
Does it still boot after the error?

Do you then have an entry in fstab as it thought there was a floppy?

Post this if you can boot:

       cat /etc/fstab

---

### Post by satimis on 2012-12-05
> **oldfred said:**
> Does it still boot after the error?

Yes.

> 
Do you then have an entry in fstab as it thought there was a floppy?

Post this if you can boot:

       cat /etc/fstab

$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=807925d7-17ae-40a1-8f2d-2790b1c9de80 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```


I have another HD on this PC(not connected at the same time) also running Ubuntu 12.04 64bit.  Ubuntu has been running for several years.  It was upgraded from 10.04/11.04/12.04.  It doesn't has this problem.

Old HD
======
$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5336d7f0-1a0d-4f37-b7d4-56b949ec03f7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=415bba81-2cfb-4f2a-92ba-3128141e3a00 /home           ext4    defaults        0       2
# /kvm was on /dev/sda4 during installation
#UUID=d3d5adde-4ad4-43c0-8d26-967c84ee583e /kvm            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f99198b1-2fc5-443f-b78d-bb9b0be13df5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Both HDs have the same storage space, 1T.

satimis

---

### Post by oldfred on 2012-12-05
Add a # to the start of this line to convert to a comment or delete this line:
> 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0       sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts::
sudo mount -a

---

### Post by satimis on 2012-12-05
> **oldfred said:**
> Add a # to the start of this line to convert to a comment or delete this line:
       sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts::
sudo mount -a
Performed following steps:

$ sudo cp /etc/fstab /etc/fstab.backup
$ gksudo gedit /etc/fstab
no warning.  Neither there is any partititon mounted manually.

$ sudo reboot

The warning is still there at boot

$ cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=807925d7-17ae-40a1-8f2d-2790b1c9de80 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by oldfred on 2012-12-05
When you run the sudo mount -a did you get any waring or did it just return to command line which says everything is ok?

If not from fstab where is it thinking you have a floppy, if you have it turned off in BIOS? BIOS does pass some parameters to system so if not off in BIOS that can cause issues.

---

### Post by satimis on 2012-12-06
> **oldfred said:**
> When you run the sudo mount -a did you get any waring or did it just return to command line which says everything is ok?

No printout/output

> 
If not from fstab where is it thinking you have a floppy, if you have it turned off in BIOS? BIOS does pass some parameters to system so if not off in BIOS that can cause issues.
On BIOS I already selected not booting floppy

satimis

---

### Post by oldfred on 2012-12-06
In BIOS it is not just the booting which is one entry, but there should be an entry for floppy installed or not. It may be called drive a:?

---

### Post by satimis on 2012-12-06
> **oldfred said:**
> In BIOS it is not just the booting which is one entry, but there should be an entry for floppy installed or not. It may be called drive a:?
I found it on BIOS;

Legacy Diskette A (set it to "disable')

-> Save -> Reboot

The warning at boot disappears.  Thanks

satimis

---

