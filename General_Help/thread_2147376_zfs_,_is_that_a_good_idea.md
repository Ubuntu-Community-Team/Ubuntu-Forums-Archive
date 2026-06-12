---
title: "zfs , is that a good idea ?"
date: 2013-05-21
forum: General Help
---

### Post by chpnp on 2013-05-21
Hi all,

I just bought a 2 gb additionnal disk for my system. I bought it because i need more room and a better backup policy.
I do not have that much data; but i certainly have had my share of data i had to restore because of accidental partial or total loss (erased or faulty disk).

I was considering to format it with a ZFS partition to have both snapshots and auto-repair (i intend to swap 2 disks like each other week to backup my disk, and keep it in a safe place)
considering also to define a truecrypt volume inside the zfs partition.

I have seen there is a ppa for zfs on unbuntu (64 bits only)

any comment why zfs could be a good/bad idea for such a system ? ease of installation (I never used it) ? 
Is is overall robust enough on ubuntu that I can trust it better than whatever else i have been using ?
Any reason to avoid truecrypt on zfs on ubuntu ?

Thanks
Have a great day !

---

### Post by tgalati4 on 2013-05-21
Give ZFS a spin and tell us of your experiences.  Truecrypt should work, but it will put extra load on your system.  Only use encryption on directories that really need it.  Is it more reliable than Ext4?  Probably not, but it does have a lot of interesting features such as checking for file integrity and comparing checksums of files as stored on the disk with file headers stored in a special filesystem location.  ZFS will not save you from accidental erasure or faulty hardware.  A good backup plan is what will save you from those two issues.

---

### Post by HiImTye on 2013-05-22
zfs for linux is in bad shape. give it some time, and it may be good, but for now if you want ZFS you should use OpenBSD

---

