---
title: "a file structure question related to disaster recovery"
date: 2006-11-06
forum: General Help
---

### Post by podunk on 2006-11-06
I didn't plan my partitions well. I have a 120 gig /home on a separate partition. On the same drive I had a 40 gig partition that I used for windows data. I converted all the windows data that I wanted to Linux, and formated the partition ext3.

I mounted this partition in my home directory like so
/home/me/dat1 

If a disaster happened to home (like rm -r for instance) it would take that partition out also wouldn't it?

If I made directory
/data
and mounted that partition there and chowned it to me - would that be a security risk of some sort? Is there a reason partitions are mounted in /media or /mnt instead of root - besides tradition that is?

---

### Post by aysiu on 2006-11-06
People mount to /media because the partition will then show up on the desktop.

I would mount to /data--that seems like a good place to put things.

---

### Post by po0f on 2006-11-06
podunk,

Yes, any filesystems mounted under /home will also be wiped out on a `rm -rf /home`.  If you plan on only having data on this partition, why not just make a /media/data mount point for it?  And you shouldn't have any problems security-wise if this is the fstab entry for it:
```
/dev/whatever /media/data ext3 noatime,noexec,nosuid,nodev 0 2
```
This is how my /tmp partition is mounted.  The following is lifted from mount's [man page](http://www.die.net/doc/linux/man/man8/mount.8.html):
[list]
[*]**noexec**: Do not allow direct execution of any binaries on the mounted file system. (Until recently it was possible to run binaries anyway using a command like /lib/ld*.so /mnt/binary. This trick fails since Linux 2.4.25 / 2.6.0.) 
nomand 
[*]**nosuid**: Do not allow set-user-identifier or set-group-identifier bits to take effect. (This seems safe, but is in fact rather unsafe if you have suidperl(1) installed.)
[*]**nodev**: Do not interpret character or block special devices on the file system.
[/list]

And mounting under /media is a little bit tradition, [a little bit standard](http://www.pathname.com/fhs/pub/fhs-2.3.html).

---

### Post by ejket on 2006-11-06
I mount a data partition that I share among distros at /home/data, then symlink it to the various /home/user directories.  Of course it could be mounted on mnt/data which is probably more logical, but at the time I wanted to keep things with user permissions under /home.

/media I reserve for removeable media.

---

### Post by podunk on 2006-11-06
Thank you all. :) I decided to go ahead and put it in media - I won't learn Linux very well if I go bucking tradtions and standards this early in the game.

Question for aysiu if you'd be so kind, I noticed that on Ubuntu my Windows drives (mounted in /media) show up on the desktop. They don't in my  Kubuntu 6.06. Is the default different between the 2 distributions or have I done something wrong?

---

