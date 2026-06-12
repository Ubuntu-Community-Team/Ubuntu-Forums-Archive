---
title: "kernel panic on reboot, VFS: unable to mount root fs"
date: 2008-05-16
forum: General Help
---

### Post by ktulu1115 on 2008-05-16
Well somehow something on my server got defunct.  I have an old Edgy (I think, maybe even Dapper, it's running 2.6.17) server I put together a few years back which ironically enough I was in the process of replacing.  I did a reboot on it and now it won't boot.  I can't think of any recent changes I've done that would impact anything of this nature.

Here's the basic setup and what I think *might*  be the cause.  It's running Server edition and I have 6 drives total.  rootfs : 2 IDE drives, part of RAID1 array /dev/md1.  I believe the partitions are /dev/hda1 and /dev/hdc1 - they seem to be the root partitions when I check within grub.  /dev/md2 (/home) consists of /dev/hda3 and /dev/hdc2 (/dev/hda2 is swap).  These partitions are of type 0xfd and 0x82 for the swap.  /dev/sd[a-d]1 are SATA drives consisting of RAID5 array /dev/md0 exported via NFS.

The error I'm getting is "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown -block(0,0)." It's also giving me "RAMDISK: ran out of compressed data"  before that.

The Grub options are:
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/md1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic

I've tried various permutations of root and kernel options pointing to different partitions and drives.  I know both drives are detected fine in BIOS and Grub can read them both as tab completion works just fine for all partitions.

What I noticed however is that booting used to give me a message similar to this:

md: autorun
md:..autorun DONE

I'm not sure if the md driver is being loaded or not, but then again maybe the boot sequence didn't get to that point.  Any ideas here?

---

### Post by ibuclaw on 2008-05-16
You could try:
```

kernel /boot/vmlinuz root=/dev/md1 ro quiet splash
initrd /boot/initrd.img

```
or
```

kernel /vmlinuz root=/dev/md1 ro quiet splash
initrd /initrd.img

```

There should be symlinks to your most recent kernel in those locations (or one of those locations).

I seem to remember getting this sort of error when I tried my first attempt at compiling the linux kernel.
Having the initrd pointing to the right location fixed it.

Regards
Iain

[EDIT]
What device is "md" by the way? I've never heard of it before. (Are they RAID devices?)

---

### Post by ktulu1115 on 2008-05-20
Sorry for the delay....   I tried both of those but without luck.  Never figured out the issue on this one.  I eventually said forget it and just moved my RAID5 array to the new server.  :)

md stands for "mirrored device" (or drive), and yes, it's the name the Linux kernel gives the device for any software RAID array.  In my example, /dev/hda1 and /dev/hdc1 compose a virtual device called /dev/md1, so to mount it you would do something like "mount -t ext3 /dev/md1 /".

I've also dome some quick researching and apparently it can be a pain to get Linux to boot of a software RAID1 array and have it be fool-proof.  I initially set up my new server with a RAID1 array again, but tried doing some disaster-recovery and booting with one of the disks removed, didn't boot.  Grub doesn't get automatically installed on both disks.  After doing that, it still wouldn't boot.

Decided to abandon that route, now I just mount the second backup drive and do rsync to keep the two mirrored.

---

### Post by fjgaude on 2008-05-21
The "md" in Linux stands for "multiple devices". The kernel code is called md and the command line tool to handle arrays is mdadm. Such is very mature and bullet proof from what I've experienced.

---

### Post by ktulu1115 on 2008-05-21
Er, sorry.  Yes I meant multiple device, not my original answer.  And yes I also agree, it is rather robust and stable from my experience as well, with my RAID 5 array at least.

---

