---
title: "/dev/.tmp-254-1 ficticious device, fsck can't check"
date: 2008-04-24
forum: General Help
---

### Post by jcummings on 2008-04-24
Hiya,

I only rarely reboot my machine, so am unsurprised when it wants to
check the drives with fsck when I haven't done so for awhile.  Earlier
this month I did so (on a machine still running Feisty) and when it
rebooted fsck ran into an error and landed in a maintenance shell.

Looking at /var/log/fsck/checkfs it has:

=====
Log of fsck -C -R -A -a
Mon Apr  7 11:10:42 2008

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/.tmp-254-1
/dev/.tmp-254-1:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
   e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/.tmp-254-2
/dev/.tmp-254-2:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
   e2fsck -b 8193 <device>

fsck died with exit status 8
=====

Of course there is no device /dev/.tmp-254-1 or .tmp-254-2 ....

The actual tmp partition seem to be controled by /dev/mapper/sda6
or in fstab:
UUID=d2ef1ca9-6964-4a64-8234-3569432ceed7 /tmp ext3 defaults 0 3

So why does fsck think there is this extra device, and how can I make
sure it boots smoothly? (I sometimes restart this machine from
remote...)

I don't think this is a problem with fsck ... it is doing what it is told.  How do I get rid of this fictitious non-existent device?  I think it might have been created at one upgrade or another.

Thanks for any helpful suggestions,

-James

---

