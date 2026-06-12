---
title: "ubuntu--vg-ubuntu--lv only 55 GB. Why?"
date: 2023-04-10
forum: General Help
---

### Post by johndid on 2023-04-10
Hi everyone,


I ran **df -h** on my Ubuntu 20.04 lts server:

```
Filesystem                         Size  Used Avail Use% Mounted on
udev                               1.8G     0  1.8G   0% /dev
tmpfs                              366M  4.0M  362M   2% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   55G   22G   31G  42% /
tmpfs                              1.8G     0  1.8G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              1.8G     0  1.8G   0% /sys/fs/cgroup
/dev/loop0                          56M   56M     0 100% /snap/core18/2714
/dev/loop1                          56M   56M     0 100% /snap/core18/2721
/dev/loop2                          64M   64M     0 100% /snap/core20/1828
/dev/loop3                          64M   64M     0 100% /snap/core20/1852
/dev/loop4                          92M   92M     0 100% /snap/lxd/23991
/dev/loop5                          50M   50M     0 100% /snap/snapd/18596
/dev/loop6                          92M   92M     0 100% /snap/lxd/24061
/dev/loop7                          50M   50M     0 100% /snap/snapd/18357
/dev/sdb2                          974M  811M   96M  90% /boot
/dev/sda1                          458G   37G  398G   9% /media/backup
tmpfs                              366M   24K  366M   1% /run/user/1000



```

It seems that I have only a 55G available, but I am sure that there is a 120 GB SSD, (yes a bit old) on my laptop.

So I ran also **fdisk -l**:



```
Disk /dev/sdb: 111.81 GiB, 120034123776 bytes, 234441648 sectors
Disk model: Crucial_CT120M50
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 87607337-xF58-xxx-xxx-xxxxxxx

Device       Start       End   Sectors   Size Type
/dev/sdb1     2048      4095      2048     1M BIOS boot
/dev/sdb2     4096   2101247   2097152     1G Linux filesystem
/dev/sdb3  2101248 234438655 232337408 110.8G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 55.4 GiB, 59479425024 bytes, 116170752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

So, Why do I have only 55 GB available?
It seems that something has been messed up with partitions/volumes when I installed Ubuntu
Thanks

---

### Post by TheFu on 2023-04-10
Is LVM new to you?
The best practice for using LVM is to allocate only the storage you need as you need it, where you need it.  For /, 55GB is much too large.  Anyone using LVM is expected to setup LVs for home, var, and any other special storage areas.

To get a feel for what your system is doing with LVM, run these 3 commands, 
```
sudo pvs
sudo vgs
sudo lvs
```
Those commands show the summary of PVs, Physical Volumes, VGs, Volume Groups, and LVs, Logical Volumes.  If you'd like help interpreting the output, post that output here  wrapped in forum 'code tags'.  I'm happy to show my LVM setups, if you like. Last fall, I setup a new 20.04 system with nearly "ideal", IMHO, LVM setups.  

```
$ sudo lvs |wc -l
28
```
So, this command shows that I have 27 LVs on that system.
```
$ sudo vgs |wc -l
10
show there are 9 VGs.
```  I typically do 1 VG per physical storage device, but not always.
Often, an LV can be considered a really, really, really, flexible partition that can be modified while the system keeps running.

Another best practice for using LVM is to leave about 50% of the storage unallocated for more advanced needs, like snapshots during backups or to have a snapshot for trying out new code that can easily be rolled back.  
Say you want to try a distro upgrade. With LVM, you can make a snapshot of the current system, then do the upgrade. If it fails or makes you unhappy in any way, you could rollback to the prior state, forgetting all those changes.  If the update makes you happy, you can merge those changes and forget the snapshot.  Very handy.  Snapshots happen instantaneous - regardless of size.  But they aren't backups. They just freeze the storage blocks used by the file system. Any changes have to be written elsewhere.

One of the best things that LVM provides is the ability to migrate an entire PV (typically a partition) to new storage WHILE the system keeps running full speed.  So, when you want to replace the SSD with a larger one, you'll need to run 1 command (pvmove) to accomplish that.

LVM is very powerful. There are many other things that can be accomplished with it. If you don't have LVM, then none of those things are possible.  For the most part, we can ignore LVM is there and just be happy 1-2 times a year when having it is really handy.

---

### Post by johndid on 2023-04-10
> **TheFu said:**
> Is LVM new to you?

Almost totally new. I just read a couple of articles about it yesterday. I've always used ext4 only. I even didn't know that such a LVM was running on my Ubuntu server.:oops: 


> 
To get a feel for what your system is doing with LVM, run these 3 commands, 
```
sudo pvs
sudo vgs
sudo lvs
```


respectively

```
 PV         VG        Fmt  Attr PSize    PFree
  /dev/sda3  ubuntu-vg lvm2 a--  <110.79g 55.39g
```

```

 VG        #PV #LV #SN Attr   VSize    VFree
  ubuntu-vg   1   1   0 wz--n- <110.79g 55.39g
```

```

 LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 55.39g
```


> 
Another best practice for using LVM is to leave about 50% of the storage unallocated for more advanced needs, like snapshots during backups or to have a snapshot for trying out new code that can easily be rolled back.  
Say you want to try a distro upgrade. With LVM, you can make a snapshot of the current system, then do the upgrade. If it fails or makes you unhappy in any way, you could rollback to the prior state, forgetting all those changes.  If the update makes you happy, you can merge those changes and forget the snapshot.  Very handy.  Snapshots happen instantaneous - regardless of size.  But they aren't backups. They just freeze the storage blocks used by the file system. Any changes have to be written elsewhere.


Uttermost interesting!
So, snapshots would be stored in the unallocated space, if I got it right.
How can I run a snapshot?
What if I run a few snapshots, and I then want to enlarge the LV, say from 55GB to 70GB? 

> 
One of the best things that LVM provides is the ability to migrate an entire PV (typically a partition) to new storage WHILE the system keeps running full speed.  So, when you want to replace the SSD with a larger one, you'll need to run 1 command (pvmove) to accomplish that.



Very good. I'd like to dive a bit deeper into this feature. It might be in handy. Do I have to plug another SSD on the same machine, then running the pvmove command and it works?

Thank you

---

### Post by TheFu on 2023-04-10
> **johndid said:**
> Almost totally new. I just read a couple of articles about it yesterday. I've always used ext4 only. I even didn't know that such a LVM was running on my Ubuntu server.:oops: 
Well, you checked a box or selected LUKs encryption. With LUKS encryption, LVM is setup.
> **johndid said:**
> 
```
 PV         VG        Fmt  Attr PSize    PFree
  /dev/sda3  ubuntu-vg lvm2 a--  <110.79g 55.39g
```

```

 VG        #PV #LV #SN Attr   VSize    VFree
  ubuntu-vg   1   1   0 wz--n- <110.79g 55.39g
```

```

 LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 55.39g
```


So, this says you have 55G assigned to the LV named "ubuntu-lv".
The PV and VG are using all of sda3, which is 110G in size.  That means you have about 55% available for other uses.  If it were me and I had just installed the system, then I'd setup swap, home and var LVs and perhaps an LV just for virtual machines and/or LXD managed containers.  A /var/ LV is important to prevent system lock ups if logs start running away.  

Also, I'd reduce the ubuntu-lv to be 25G-35G.  IME, 35G is fine for desktops, but overkill for servers.  55G is crazy huge for either.  The way we setup our storage directly related to how we will do backups, disaster recovery and how easy system upgrades to new versions of the OS can be.

> **johndid said:**
> 
Uttermost interesting!
So, snapshots would be stored in the unallocated space, if I got it right.

Wrong. snapshots are groups of existing, frozen, blocks of storage from a specific point in time. Nothing is moved. It is frozen and cannot be modified. If the files aren't modified, then no more storage is used. If files are modified, those modificatation have to be written into unallocated areas. This is why the snapshot gets a size parameter at creation.  TLDP has a good explanation of snapshots with a very simplified backup method.  [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

> **johndid said:**
> 
How can I run a snapshot?
What if I run a few snapshots, and I then want to enlarge the LV, say from 55GB to 70GB? 
You shouldn't. Enlarge it. You should create new LVs, put a file system on them as needed/desired, then mount those new file systems where needed.

> **johndid said:**
> 
Very good. I'd like to dive a bit deeper into this feature. It might be in handy. Do I have to plug another SSD on the same machine, then running the pvmove command and it works?

You need to review the **pvmove** manpage. It is one of the easier commands, but it isn't magic. You are expected to be the administrator still.

---

### Post by johndid on 2023-04-10
> **TheFu said:**
>  


Wrong. snapshots are groups of existing, frozen, blocks of storage from a specific point in time. Nothing is moved. It is frozen and cannot be modified. If the files aren't modified, then no more storage is used. If files are modified, those modificatation have to be written into unallocated areas. This is why the snapshot gets a size parameter at creation.  TLDP has a good explanation of snapshots with a very simplified backup method.  [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)


You need to review the **pvmove** manpage. It is one of the easier commands, but it isn't magic. You are expected to be the administrator still.

Ok, I just need to learn more about it before I start practising with it.
 Thanks for your advice and the link

---

### Post by TheFu on 2023-04-10
> **johndid said:**
> Ok, I just need to learn more about it before I start practising with it.
 Thanks for your advice and the link

Snapshots prevent space that would normally be reuse from being modified or available.  We can't have snapshots forever. Eventually, we'd run out of space due to all the blocks being frozen.

---

