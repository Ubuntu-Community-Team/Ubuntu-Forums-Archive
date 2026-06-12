---
title: "PC froze &amp; I did a REISUB too quicky, now &quot;Kernel Panic : VFS: unable to mount root &quot;"
date: 2023-06-15
forum: General Help
---

### Post by gbp00 on 2023-06-15
searched this on DDG "what to do when ubuntu freezes"

pinned answer was 

 If it locks up completely, you can REISUB it, which is a safer alternative to just cold rebooting the computer. 
   REISUB by: 
   While holding Alt and the SysReq (Print Screen) keys, type REISUB. 
  R:  Switch to XLATE mode
E:  Send Terminate signal to all processes except for init
I:  Send Kill signal to all processes except for init
S:  Sync all mounted file-systems
U:  Remount file-systems as read-only
B:  Reboot

when I checked comments (after), it was clear you had to wait 2 seconds between each command...

Now there's a kernel offset; a Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown block, when booting into recovery mode / normal.
I've got the USB & hoping ya'll will help with some Grub magic

---

### Post by ajgreeny on 2023-06-15
You may be able to get through this by booting to a live system from the USB you used to install Ubuntu then running command ```
sudo e2fsck /dev/sdx#
```
where sdx# is the root partition of your installed system which you should be able to find from command ```
sudo blkid -c /dev/null
```.

Come back again if that doesn't make sense to you or simply fails to solve the problem.

---

### Post by gbp00 on 2023-06-15
Here is result:

> /dev/sda2: UUID="0AE0-3298" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="..."
/dev/sda3: UUID="..." BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="..."
/dev/sda1: PARTUUID="..."
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda3
e2fsck 1.46.5 (30-Dec-2021)
/dev/sda3 is mounted.
e2fsck: Cannot continue, aborting.


ubuntu@ubuntu:~$ sudo e2fsck /dev/sda2
e2fsck 1.46.5 (30-Dec-2021)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

/dev/sda2 contains a vfat file system
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda3
e2fsck 1.46.5 (30-Dec-2021)
/dev/sda3 is mounted.
e2fsck: Cannot continue, aborting.


ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.46.5 (30-Dec-2021)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>



---

### Post by Rubi1200 on 2023-06-15
Please post the output from the Boot info script in my signature. Note, do not try and repair, just post the results to give us a better overview.

Also, just to clarify: did you run fsck from a liveUSB with filesystems unmounted?

---

### Post by MAFoElffen on 2023-06-15
[QUOTE=Rubi1200;14147082]Please post the output from the Boot info script in my signature. Note, do not try and repair, just post the results to give us a better overview.

[COLOR=#b22222]Also, just to clarify: did you run fsck from a liveUSB with filesystems unmounted?[[/COLOR]/QUOTE]
From his output, which doesn't make sense:
```

/dev/sda2: UUID="0AE0-3298" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="..."
/dev/sda3: UUID="..." BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="..."
/dev/sda1: PARTUUID="..."
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda3
e2fsck 1.46.5 (30-Dec-2021)
/dev/sda3 is mounted.
e2fsck: Cannot continue, aborting.

```
It was saying that /dev/sda3 was mounted... If he was booted from a LiveUSB, you would thing it would be  similar to this:
```

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop1: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/sr0: BLOCK_SIZE="2048" UUID="2023-02-23-04-13-44-00" LABEL="Ubuntu 22.04.2 LTS amd64" TYPE="iso9660" PTTYPE="PMBR"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/vda2: UUID="8583c172-9c53-467e-be43-18d8ee5b4a01" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="fb4a7bcd-425e-436e-bd78-88df14066cb1"
/dev/vda3: UUID="eec74ce7-e2c3-435d-bf75-a7d503859790" TYPE="crypto_LUKS" PARTUUID="b71836a5-18f3-435e-817c-6797ca9dc6e0"
/dev/vda1: UUID="DAC2-E709" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="40fc046c-2784-4e2f-879e-05c6861d37ea"
/dev/loop3: TYPE="squashfs"

```
Yes, it was cutoff... But look at his /dev/sda1, the output is "invalid". Yes, curious to see what the 'boot-info' report says. Waiting for him posting the URL of the pastebin.

---

### Post by gbp00 on 2023-06-15
RE: "Just to clarify: did you run fsck from a liveUSB with filesystems unmounted?"
I do not know. Didn't receive the obligatory Linux for Dummies on my system.

Whoops, saw the "Do Not Touch Things" a little late.

Already followed these instructions.
> 

Start with a livecd, open a a terminal and execute:

sudo fdisk -l
sudo mount /dev/sdax /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt 

If you /boot is on a separate partition also call:

sudo mount /dev/sday /mnt/boot

and now you can make update-initramfs and update-grub without errors.

update-initramfs -u -k 2.6.38-8-generic (or your version)

If you don't know your version. Use:

dpkg --list | grep linux-image

And just update Grub.

update-grub

Reboot your system.



here are results :) did not try boot repair as instructed.

[https://paste.ubuntu.com/p/xfv83qFSqG/](https://paste.ubuntu.com/p/xfv83qFSqG/)

---

### Post by gbp00 on 2023-06-15
Some assistance please?

---

### Post by MAFoElffen on 2023-06-16
I see a few things...

First thing to do is tell us what this is on.

Next, boot your computer and check the BIOS boot mode, ad see why it is boot Legacy / CSM.

The install of Ubuntu on this machine is both EFI boot, and Legacy boot. Yes, it is multi-mode boot capable.

Somewhere along the line, someone took the time and efoort to get this installed manually on this GPT disk, so that sda1 is bios_boot (to be able to be boot as Legacy boot mode), sda2 is EFI (to be boot in UEFI boot mode), and /dev/sda3 is the system root... That doesn't happen with a default install. They took the extra effort so that it could be boot on many systems, no matter what the BIOS was capable of.

The Grub part1 in the MBR, points to the start of that bios_boot partiton, where the boot.img is, that then points to /dev/sda3/boot/

The EFi partition has only Ubuntu installed EFI boot files. I see not trace of Windows remnants on the disk. 

I think that somehow, something toggled the BIOS boot mode to Legacy boot... It should also boot in Legacy, but what I see of the system and layout, it should most probably be booting from EFI. Reset the BIOS back to boot from UEFI mode. That in itself might fix it outright. 

I see an ext4 filesystem on the root disk, /dev/sda3... Whether that filesystem is healthy at this point is still suspect. The OP tried to do fsck on that partition with it mounted. That was the error in his output. If on a LiveUSB, if he tried looking at the partition in a file manager, it would have mounted that disk, that is what I think happened with that. He didn't know that he should have unmounted the partition, before doing the fsck. I think he needs to do that again (from a LiveUSB). It errored out, while trying to make a filesystem repair... I would feel better if he just redid that and make sure this time it doesn't error out again.

If it "then", didn't boot, then we know that the BIOS is set in the right mode, that /dev/sda3 has a good filesystem, to be able to reinstall Grub-- Mounting the partitions of the installed filesystem and chroot into the installed system to reinstall GRUB2 as EFI.

I don't know "how" this problem happened, and what happened in the past really doesn't matter. What does matter is getting you going again. After we get you booting again dependably... Then you can start a different thread to fix your original problem, which is intermittent freezing. Right?

EDIT:
If someone is wondering what <Alt><Sysreq><Command-Key> reisub is about, RE: [https://www.kernel.org/doc/Documentation/admin-guide/sysrq.rst](https://www.kernel.org/doc/Documentation/admin-guide/sysrq.rst)

---

