---
title: "Swap and LVM"
date: 2008-02-20
forum: General Help
---

### Post by ZeroZ400 on 2008-02-20
Just installed Xubuntu on an old P3 1Ghz with 128MB of ram.  The swap was set to 364MB by default, I wanted to make it larger.  I decreased the size of the root volume size and increased the swap volume.  

But the output of swapon -s doesn't show this:
```
root@dinosaur:/dev/mapper# swapon -s
Filename                                Type            Size    Used    Priority
/dev/mapper/dinosaur-swap_1             partition       372728  91972   -1
```

So, does LVM use a swap file instead of something more like a swap partition?  If it does, how do i make the swap file bigger?
I also tried turning off swap which failed.  So this may make things even more difficult:
```
root@dinosaur:/dev/mapper# swapoff -a
swapoff: /dev/mapper/dinosaur-swap_1: Cannot allocate memory
```

Here's some more info:
```
root@dinosaur:~# lvdisplay 
  --- Logical volume ---
  LV Name                /dev/dinosaur/root
  VG Name                dinosaur
  LV UUID                lbWvJT-RFUe-BHIG-0gW1-fiLy-bBWZ-MzH16x
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                35.00 GB
  Current LE             8960
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0
   
  --- Logical volume ---
  LV Name                /dev/dinosaur/swap_1
  VG Name                dinosaur
  LV UUID                ldluB2-1PSo-h8Q8-Y5YK-uhfa-Du7l-SAssWh
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                2.00 GB
  Current LE             512
  Segments               2
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:1
```

So, how do I get my to use all 2GB of swap and get around swapoff not working.  Thanks.

---

### Post by ZeroZ400 on 2008-02-28
Ideas anyone?

---

