---
title: "Ubuntu boots only if I leave external (USB) drive connected"
date: 2018-01-02
forum: General Help
---

### Post by michael351 on 2018-01-02
I have an external data drive (for Kodi movies, music only) that is connected to my Ubuntu system via USB.
It works fine.

However, if I try and boot the machine (Acer Aspire) without the hard drive connected, Ubuntu fails to boot and instead puts me in a recovery mode.

Any help on why it might be doing this and what I can do to diagnose? I need to move the PC to a different location temporarily and didn't want to take the hard drive with me as it's not needed.
The OS is installed on the internal HDD. It should just boot up ...

Thanks

---

### Post by TheFu on 2018-01-02
Check your /etc/fstab file.  If it isn't using UUIDs, then the order of the boot devices connected could easily change and prevent the correct disk from being found.

There are how-tos for fstab files. Google will find them.

Of course, this assumes that the USB storage isn't used for any purpose necessary for booting the OS.

---

### Post by yancek on 2018-01-02
Which release of Ubuntu are you using?  Is Ubuntu the only OS you have?  Is this an older MBR install or UEFI/GPT?
As far as diagnosing, if you don't resolve this google 'boot repair ubuntu' and go to the site and download and run the boot repair software using the 2nd option with the ppa.  Post the link they give when you finish which will contain details on your system.

---

### Post by oldfred on 2018-01-02
If BIOS based system and all of system is on internal drive, grub may be installed on external?
If UEFI, it would be unusual that you need external unless system is installed on external drive.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by michael351 on 2018-01-02
Grub is internal and it does load. I select Ubuntu from there and it starts to load and then drops me into a recovery shell. From there I should be able to check the fstab.
There are no OS files/system on the secondary drive. Is is only for user data.

When I connect the second drive, however, all is normal.

I'll post what I find out.

---

### Post by michael351 on 2018-01-04
In the fstab the external USB drive is first to get mounted. Since I disconnected it, I wonder if that is the reason the boot process stops and puts the system into "emergency mode"?
I can examine the system in this mode (the OS is responsive to commands). I wonder if I can just issue a command to continue the boot process to bring me to a login screen?

---

### Post by TheFu on 2018-01-04
If you need help with the fstab file, post it here. There are some settings that let boot continue after a failure.

Or there is always the manpage for the fstab file which explains all of this.

---

### Post by michael351 on 2018-01-04
Below is my fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=24af3e43-a0b1-4376-87b7-7c0cfad2d050 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=b93d264a-92c0-4646-90c9-052cc0f12021 none            swap    sw              0       0
 
# Mount USB drive /dev/sdb1
UUID=88C2D23DC2D22F66 /media/user/ Home_Theatre ntfs uid=1000,gid=1000,dmask=022,fmask=133 0 0


It does seem that /dev/sdb1 is causing my system to go into "emergency mode" when the disk is unplugged. I haven't tested yet what would happen if I comment out this line for when I disconnect the drive.

---

### Post by oldfred on 2018-01-04
I am pretty sure it used to boot with an error in fstab (as long as not /), but had to time out.
But lately we have seen a lot of boot issues with fstab that is not correct or partition UUID wrong or like yours.

You can comment out.
Normally we do not mount drives we disconnect in fstab, only internal devices.

If you label sdb1 it will mount under the label if clicked on, or you can create a small script to mount manually.
Default mounts now are /media/$USER/UUID or label if found.

---

### Post by TheFu on 2018-01-04
Change the line to 

```
UUID=88C2D23DC2D22F66 /media/user/Home_Theatre ntfs uid=1000,gid=1000,dmask=022,fmask=133 0 2
```

BTW, the line you posted has an extra space in front of "Home".  This could easily cause problems, even when connected.  The directory where a device is to be mounted must exist.

The '2' which replaced the '0' at the end of the line has a specific meaning.  0, 1, 2 are valid values for that location. From the manpage:```

       The sixth field (fs_passno).
              This field is used by the fsck(8) program to determine the order
              in which filesystem checks are done at reboot  time.   The  root
              filesystem  should be specified with a fs_passno of 1, and other
              filesystems should have a fs_passno of 2.
```

Hope this is helpful.  By using the UUID for mounting, any change to ports used or order that the OS discovers each storage partition/LV doesn't matter.  The comments for where the storage was during the installation is slightly helpful, but should always be validated if you need to do things using the device name directly.  Those devices DO move around, which is why UUIDs have been the default for over a decade.

And just to answer the question - you can comment out the ntfs line, if you like.  I wouldn't.  I'd be more likely to use the "noauto" option.  Actually, that isn't true.  For any USB connected storage, I don't use the fstab.  I use autofs, which mounts storage only as needed/requested, then umounts it after a timeout period when the storage isn't used.

---

