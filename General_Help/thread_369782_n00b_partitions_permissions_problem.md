---
title: "n00b partitions permissions problem"
date: 2007-02-24
forum: General Help
---

### Post by rkang on 2007-02-24
So I have an 80GB main partition hdf1, 5 GB extended partition hdf2 with a 5GB swap partition hdf5 nested.  I also have a 300GB storage partition hdf3 (for some reason I'd get a Grub error when using too large a space for the boot partition).

I simply want to mount hdf3 in my /home/ directory so that I may read/write/access it.  Using:

sudo mount -t ext3 /dev/hdf3 /home/username/

only gives access to the /root user.
I this is such a trivial problem yet I can't seem to figure it out.
Thanks.

---

### Post by Strider on 2007-02-25
Check out the man pages for "mount".  There's an option where you can specify which user has permission to the partition on mounting.  You can also add the mount to /etc/fstab, set the user option, thus allowing a regular user to mount the partition without requiring sudo.

-Mike

---

