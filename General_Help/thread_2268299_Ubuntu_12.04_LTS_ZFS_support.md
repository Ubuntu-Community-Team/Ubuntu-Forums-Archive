---
title: "Ubuntu 12.04 LTS ZFS support?"
date: 2015-03-07
forum: General Help
---

### Post by burgundy on 2015-03-07
For a while now, it seems that support for the native zfs kernel module in Ubuntu 12.04 has been fading.  My updater has been warning me that certain updates weren't compatible with the newest kernels and it wasn't updating them.. well a couple days ago, I installed some updates, and it looks like something got by the compatibility check and broke my ZFS kernel module.

Whenever I do zpool anything I get:
"
Failed to load ZFS module stack.
Load the module manually by running 'insmod <location>/zfs.ko' as root.
"

My uname -r returns "3.2.0-77-generic" .

A post somewhere suggested I do a:

sudo apt-get remove `uname -r` zfs-dkms ubuntu-zfs
sudo apt-get install `uname -r`
sudo apt-get install zfs-dkms ubuntu-zfs

and reboot, but backport broken package conflicts are stopping me. on the "sudo apt-get install `uname -r`".

What is the last, best, Ubuntu 12.04 kernel that supports ol' ZFS?

How do I setup my ubuntu to then load that kernel?
My grub doesn't do much because of the EFI BIOS  tricks going on with new motherboards.

Also.. while trying to fix this, my update manager says I'm completely up to date with nothing held back (probably a bad thing).  And "sudo apt-get install ubuntu-zfs" thinks everything is just fine.

I had a 1.5TB mirror of data in my ZFS pool... how am I supposed to recover from this?

Thanks for the help, also if this is the wrong place to ask, just point me in the right direction.

---

### Post by yogaman69 on 2015-05-01
Hi Burgundy,
I find myself in the exact same situation, did you ever get to a solution?

thank you

---

