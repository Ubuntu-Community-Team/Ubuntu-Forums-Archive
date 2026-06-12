---
title: "No longer able to boot RAID1 system"
date: 2015-08-01
forum: General Help
---

### Post by blong-fiction on 2015-08-01
I have an ubuntu box that I recently upgraded from 12.04LTS to 14.04LTS.  It had two disks in it with the standard three partitions (boot/swap/data), all RAID1.  Upgrade went fine, no problems.  

Recently, I installed a second pair of disks and made them a single RAID1 volume.  Installation and everything went fine, almost positive that I rebooted at least once and it booted fine.

I was recently rebooting to clear a bad NFS connection to my dead NAS.  I had done a apt-get update/upgrade to update before the reboot.

Now, the server doesn't reboot any more.  It continuously prints:
incrementally starting raid arrays
mdadm: Create user root not found
mdadm: create group disk not found
incrementally started raid arrays

This appears to be [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1335642](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1335642)

That said, it appears that's a generic issue, searching around finds many many ways in which people have fixed this.  I know some of them don't apply, ie my devices are /dev/md# in mdadm.conf.  The drives are also SATA, so I don't think it's the mpt2sas.ko issue.

Any ideas?

---

### Post by blong-fiction on 2015-08-02
ok, apparently I was dumb, I must have followed the usual rule for updating the mdadm.conf with [COLOR=#000000][FONT=Verdana]mdadm --examine --scan >> /etc/mdadm/mdadm.conf and that added to the existing file making double ARRAY entries, which I guess it didn't like (even though they were nearly identical)

Removing the extra entries, and it rebooted fine.

I definitely think the boot script is hiding the real errors making these issues more difficult to diagnose.[/FONT][/COLOR]

---

