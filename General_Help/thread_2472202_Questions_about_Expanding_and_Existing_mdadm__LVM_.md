---
title: "Questions about Expanding and Existing mdadm / LVM Array"
date: 2022-02-20
forum: General Help
---

### Post by rsteinmetz70112 on 2022-02-20
I am expanding an existing mdadm /LVM array. 

I have installed two new larger hard drives and copied the original drive partition table to them.

I have marked one of the old drives as failed, removed it from the array and replaced it with a new drive The array synced back up.

I after the array synced I marked the other old drive as failed and removed it from the array and added the second new drive back. It is syncing up now. 

I now have an array with two drives but each drive now has a large amount of unpartitioned space. 

I think I next need to use parted to increase the partition size on both drives.

Then use vgextend to extend the volume group 
Finally use lvextend to make the volumes bigger.

My question is can this be done on an active system, that is one which is currently in use or should I shut down everything first, or did I already screw up?

---

### Post by TheFu on 2022-02-22
There are at least 2 different methods.

What you've outlined above will end up with a cleaner outcome, but because a partition is being changed, downtime is mandatory. Start from the hardware and move in to increase the size of the file system. Changing the file system is last.   Don't skip any layers. Because partitions are involved, you'll need to take them off-line.

Or

You can create new partitions (same size on the disks for mdadm needs, not as the existing partitions), create a new RAID array using those, add the PVs (on the new mdadm array) to the existing VG and let LVM resize/extend into the the other array as you like. It is a little messy, but that might not matter.  I have a VM system where I did something similar with LVM by adding another virtual HDD to the VM.  Some day, I should create a single, larger vHDD and migrate everything from the 2 older vHDDs over.  Someday.  OTOH, I was able to add new storage without ever taking the system down or interrupting any active operations. Here's my 2-disk, spread LVM setup.
```
$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  root   vgubuntu-mate -wi-ao---- 19.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g  

$ sudo vgs
  VG            #PV #LV #SN Attr   VSize  VFree
  vgubuntu-mate   2   3   0 wz--n- 39.49g 4.39g

$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree
  /dev/vda5  vgubuntu-mate lvm2 a--  <29.50g    0 
  /dev/vdb1  vgubuntu-mate lvm2 a--  <10.00g 4.39g
```
Kinda ugly, right?  I'm not a fan of spanning LVs across separate physical devices (except with for RAID1 /10 reasons). Long ago, I lost 80% of my data when 1 drive out of 3 in an LVM single VG died.  In my example above, and in your situation, we are really using 1 physical disk for the same VG, so that rule doesn't get broken.  Also, if you have excellent backups, the rule can be relaxed too.  My data loss incident was before I got backup religion. ;(

Trade-offs.

Don't forget when using lvextend, to add the -r switch, so the file system gets resized at the same time. It is very common for people to forget that part.

---

### Post by rsteinmetz70112 on 2022-02-22
I'm increasing the size of one of the LVs, and I want it bigger than the available space.I've already replaced the drives and transferred the md and data to the new drives. I still have the old drives with the data on them. Now I want to increase the size of the PV VG and LV.  I'll be able to take it down after lunch to mess with the partition table and the VG

---

### Post by MAFoElffen on 2022-02-24
You two forgot an earlier step, which TheFu started to touch on in Post #2, then I think you two got distracted. It is actually uglier than described. This is going to sound odd, like against what we were originally taught, when you first setup the array so be patient.

Start out with a good backup!!! This is risky so... This will work for RAID1 arrays... First things will be to increase the size of the individual components (the underlying partitions).

At a terminal prompt, ensure that the Array is synchronized and consistent
```

cat /proc/mdstat

```
Make sure is is through with any synchronizations... Then fail and remove one device member.
```

sudo mdadm /dev/md0 --fail /dev/sda2 --remove /dev/sda2

```
Increase the size of that removed partition with a partitioner. You can work on it, as it is offline. This may be a different larger disk that was cloned, then the partitions expanded.

Re-add the partition back to the Array... This is were it seems odd, the partitions at this point are different sizes... Will describe whathappens after the command...
```

sudo mdadm -a /dev/md0 /dev/sda2

```
Check to make sure it finishes synchronizing... 
```

cat /proc/mdstat

```
What happens here, it that newly synchronized member of the array will be the original size. Then repeat the process with the next member... Until done. You will end up with an array the original size, within the larger partitions.

Recheck that synchronization is complete. 
```

cat /proc/mdstat

```
Then check the size of the array.
```

sudo mdadm -D /dev/md0 | grep -e "Array Size" -e "Dev Size"

```
Then grow the array to the full size of the partitions
```

sudo mdadm --grow /dev/md0 -z max

```
Recheck the size of the array and device
```

sudo mdadm -D /dev/md0 | grep -e "Array Size" -e "Dev Size"

```

Then use the commands and instructions from TheFu to increase the partitions within the Array, the LVM (PV,) VG, LV and then the filesystems within them...

---

### Post by rsteinmetz70112 on 2022-02-24
Thanks for that. 

I've actually already increased the partition sizes exactly has you have suggested. I'm away from the site for a few says so when I get back I'll continue.
 
But I haven't yet increased the MD, PV, VG or LV sizes. 

You have given me the commands to increase the MD,

I think to increase the PV I need to run the following commands to first deactivate the LV, then increase the PV finally reactivate the LV:
```
# lvchange -a n /dev/<vgname>/<lvname> 
# pvresize /dev/sdxx
# lvchange -a y /dev/<vgname>/<lvname> 
```

The increase the LV size with 
```
# lvresize -r -l 100%FREE  /dev/<vgname>/<lvname>
```

One remaining question is whether I need to specifically increase the VG size prior to increasing the LV, since there are more that one LVs, but I only want to increase the size of 1.
Most of the documentation skips over that point but some says that lvresize will increase the size of the VG.

The final question (I hope) is whether like partitions the space for LVs need to be continuous or will LVM2 handles discontinuous LVs?

---

### Post by TheFu on 2022-02-24
LVM handles discontinuous LVs fine. That's why we can use lvextend 50 times across 3 LVs, if the VG has room.

---

### Post by MAFoElffen on 2022-02-24
> **rsteinmetz70112 said:**
> I think to increase the PV I need to run the following commands to first deactivate the LV, then increase the PV finally reactivate the LV:
```
# lvchange -a n /dev/<vgname>/<lvname> 
# pvresize /dev/sdxx
# lvchange -a y /dev/<vgname>/<lvname> 
```

The increase the LV size with 
```
# lvresize -r -l 100%FREE  /dev/<vgname>/<lvname>
```

One remaining question is whether I need to specifically increase the VG size prior to increasing the LV, since there are more that one LVs, but I only want to increase the size of 1.
Most of the documentation skips over that point but some says that lvresize will increase the size of the VG.

The final question (I hope) is whether like partitions the space for LVs need to be continuous or will LVM2 handles discontinuous LVs?

Yes, the VG (vgextend). That is what I see missing from your posted commands.

Think of everything as Russian Nested Dolls... That is how i used to teach it to Computer Science Students. In order, the conceptualized nested containers of, can only be as large as the inside of what it is within. 
[LIST=1]
[*]The MD device can only be as large as the room it has within the partitions it resides in. 
[*]The LVM type partitions of, can only be a large as the MD devices it resides in allows. 
[*]The PV can only be as large as those LVM type partions allow (or to be added to the PV Extents) 
[*]The VG can only be as large as space allows within the PV it resides in. 
[*]The LV can only be as large as space allows from the VG it resides in. 
[*]The filesystem can only be as large as the LV space within the LV. 
[/LIST]

Between each step, you can use tools and utilities to determine the free space to help guide you.

So to grow, you start with the largest container first and go through each, until the end to fill each. To shrink, you start at the other end, at the smallest, most inner piece.

---

### Post by rsteinmetz70112 on 2022-03-05
Just a note to confirm that I got everything to work and now have expanded the storage as I intended. I still have some reallocation to do but I arrays, PVs, VG, and LV have been extended and everything is working as expected. 

Thanks to everyone who pitched in. I'm sure your help, advice and explaination prevented me from doing this over a few time,

I'm going to make the thread solved.

---

