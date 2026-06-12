---
title: "PV reported missing but PV does not exist."
date: 2014-11-30
forum: General Help
---

### Post by scottmccarthy66 on 2014-11-30
Okay so I'm a Windoze convert and sooo glad I did.  I'm currently having difficulty with LVM.   I have two disks in a VG created on a previous install with a different computer name.  Before I gained a better understanding of LVM and the virtue of 'vgexport', I disconnected the aforementioned drives and re-installed Ubuntu after some botched tinkering.  

Now, vgscan gets:

root@Jupiter:~# vgscan --verbose
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
  Reading all physical volumes.  This may take a while...
    Finding all volume groups
    Finding volume group "stuff-vg"
    There are 1 physical volumes missing.
  Found volume group "stuff-vg" using metadata type lvm2
    Finding volume group "ubuntu-vg"
  Found volume group "ubuntu-vg" using metadata type lvm2
    Finding volume group "newstuff-vg"
  Found volume group "newstuff-vg" using metadata type lvm2

"ubuntu-vg" is the default LVM install.  

"newstuff-vg" is the VG associated with the latest install and is currently comprised of a single LV 'newstuff-lv' on a 500GB disk.  

"stuff-vg" is the VG associated with the previous install; comprised of a single LV 'lvstuff' on two drives - 1.0TB and 2.0TB.  I can access and mount the data (movies) using 'vgchange --partial'.  I have verified access by playing movies located on these disks.

How can I:
1. eliminate the errant PV being reported?
2. ensure the data is not lost?
3.  bring 'lvstuff' back into the fold?

---

