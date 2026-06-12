---
title: "Using Feisty live CD as rescue disk for LVM on RAID"
date: 2007-04-26
forum: General Help
---

### Post by waster on 2007-04-26
I am trying to recover an LVM on RAID, but it seems that running a Feisty CD doesn't have working LVM. I can apt-get install lvm2 and mdadm, I can see the MD RAID arrays, but

which lvscan 

points to /sbin/lvscan which complains that the LVM version is wrong.

What's happening? Should I use a different rescue CD?

Thanks.

---

### Post by joebaker on 2007-05-03
I knew this would come back to byte me.  Our LTSP server's root file system is LVM on top of RAID and something happened and now it won't boot.  I had been hotplugging a USB to ISA adaptor into the box so I could image the drive of a failing system.  Then when I tried rebooting the LTSP server it came up with a busybox prompt.  The LTSP server was a 6.10 system and the home directories are mounted over NFS, so I'm not in such bad shape.

But I thought that I'd add my two cents that being able to access these files *is important.*  In my case I think I can get by without the drives.  Lucky Me.

-Joe

---

