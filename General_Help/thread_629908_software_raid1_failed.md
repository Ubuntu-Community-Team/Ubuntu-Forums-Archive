---
title: "software raid1 failed"
date: 2007-12-02
forum: General Help
---

### Post by Nullexe on 2007-12-02
Hi everyone,


I have been running an Edgy fileserver for about 6 months now.  When I came home from work last week I found my files all inaccessible.  After investigation I found issues with my PV.  I would like to recover my data and replace the drives if possible any help is greatly appreciated!

I have one system drive and 6 storage drive, all raid1.  The storage layout is

2x160GB /dev/md0
2x250GB /dev/md1
2x250GB /dev/md2

After investigation I found problems with my lvm.  pvdisplay showed: 

   Couldn't find device with uuid 'xjWU5M-G3WB-tZjB-Tyrk-Q7rN-Yide-1FEVh3'.

I ran the command

   sudo pvcreate --uuid "xjWU5M-G3WB-tZjB-Tyrk-Q7rN-Yide-1FEVh3" --restorefile /etc/lvm/archive/fileserver_00006.vg /dev/md2

This seemed to recover /dev/md2.  I re-ran pvdisplay and got

  Couldn't find device with uuid '1ATm8s-oxKG-nz0p-z1QA-a0s4-od9T-AMZRoo'.

I figured I could run the same command on md1,

  sudo pvcreate --uuid "1ATm8s-oxKG-nz0p-z1QA-a0s4-od9T-AMZRoo" --restorefile /etc/lvm/archive/fileserver_00006.vg /dev/md1

and got the message:

  Couldn't find device with uuid '1ATm8s-oxKG-nz0p-z1QA-a0s4-od9T-AMZRoo'.
  Device /dev/md1 not found (or ignored by filtering).

Here is my pvdisplay.  Again, any help is Greatly appreciated
***START***

  Couldn't find device with uuid '1ATm8s-oxKG-nz0p-z1QA-a0s4-od9T-AMZRoo'.
  Couldn't find device with uuid '1ATm8s-oxKG-nz0p-z1QA-a0s4-od9T-AMZRoo'.
  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               fileserver
  PV Size               149.05 GB / not usable 0   
  Allocatable           yes 
  PE Size (KByte)       4096
  Total PE              38156
  Free PE               9996
  Allocated PE          28160
  PV UUID               pZV1Ff-Y7fu-S8m1-tVFn-fOMJ-VRls-fLFEov
   
  --- Physical volume ---
  PV Name               unknown device
  VG Name               fileserver
  PV Size               232.88 GB / not usable 0   
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              59618
  Free PE               0
  Allocated PE          59618
  PV UUID               1ATm8s-oxKG-nz0p-z1QA-a0s4-od9T-AMZRoo
   
  --- Physical volume ---
  PV Name               /dev/md2
  VG Name               fileserver
  PV Size               232.88 GB / not usable 0   
  Allocatable           yes 
  PE Size (KByte)       4096
  Total PE              59618
  Free PE               9156
  Allocated PE          50462
  PV UUID               xjWU5M-G3WB-tZjB-Tyrk-Q7rN-Yide-1FEVh3

---

### Post by Nullexe on 2007-12-04
bump

---

