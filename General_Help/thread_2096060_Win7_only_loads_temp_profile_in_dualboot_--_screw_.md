---
title: "Win7 only loads temp profile in dualboot -- screw up with ntfs-config"
date: 2012-12-18
forum: General Help
---

### Post by hmlhmlhml on 2012-12-18
Hi all

It's been ages since I'd used Ubuntu. Without doing enough reading I installed ntfs-config to read my win7 files.

I realize the error of my ways. I've been all over the forum and have edited my fstab to # out the ntfs partitions (and deleted the empty folders in /media. I purged ntfs-config. I reinstalled it. Not sure what else to do.

When I load (which is going really slow) the first thing I see is an NTFS: No Wubildr error. I can get into Ubuntu just fine and can even see my windows files. But I can't get them in Windows.

This is the result of blkid:

```

/dev/loop0: UUID="a6eece84-8179-4998-be7d-08085c5290d4" TYPE="ext3" 
/dev/sda1: LABEL="System" UUID="521827721827546F" TYPE="ntfs" 
/dev/sda2: LABEL="Windows" UUID="C238444738443D23" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="661A69671A693569" TYPE="ntfs" 
```

here is what my fstab looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/host/ubuntu/disks/swap.disk	none	swap	sw	0	0

```

a million thank you's for someone who can help.

---

### Post by oldfred on 2012-12-19
Almost all of the gui tools to edit fstab have not be well maintained.

Ubuntu has been using UUIDs as the better way to mount partitions, but         NTFS Config not updated to use UUID's.

Do you still have ntfs-3g installed?
       
 On April 12, 2011 it was announced that Ntfsprogs project was merged with NTFS-3G
[http://en.wikipedia.org/wiki/Ntfsprogs](http://en.wikipedia.org/wiki/Ntfsprogs)
# Do not do this as on newer versions it uninstalls ntfs-3g
sudo apt-get install ntfsprogs

Also you have wubi which works a little different. You should see all your Windows in hosts.

 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

