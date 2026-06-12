---
title: "How to use LVM volume?"
date: 2019-05-03
forum: General Help
---

### Post by lbunch on 2019-05-03
I let the new Ubuntu Server installation automatically install with LVM.  Mistake.  The 2TB drive is all one physical volume (PV) and one Volume Group (VG) (ubuntu-vg) with just a tiny Boot volume and a root volume, ubuntu-lv.  New to LVM, I read about it and resized the system volume to 25GB.  Then I created a Storage volume of 1.0 TB.  

The system is at /dev/mapper/ubuntu--vg-ubuntu--lv.   Everything under / is accessibly normally.  
My data volume lists as /dev/ubuntu-vg/Storage. I cannot access this in any way, but it shows on lvdisplay, etc.

How do I mount this volume so I can use it for data storage on the server and access it on the network from my other linux machines?  I find nothing about that, and my experience with previous partitioning doesn't help much.   The server is command line only.

Thank you.
Les

---

### Post by TheFu on 2019-05-03
Where ever you would put /dev/sdaX in the fstab, put the path to the new LVs you've created.

Here's one of mine:
```
UUID=d62de6a2-5b69-4d3a-8a31-91040d274d9e /boot ext2 defaults,noatime     0  2
UUID=E7E6-D023  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--vg-root /       ext4  noatime,errors=remount-ro 0  1
/dev/mapper/ubuntu--vg-home--lv /home   ext4 errors=remount-ro,noatime 0 2
/dev/mapper/ubuntu--vg-stuff    /stuff  ext4 errors=remount-ro,noatime 0 2 
/dev/mapper/ubuntu--vg-swap_1   none      swap    sw              0       0
```

Learn to use the 3 different layers in LVM
* PV (also called PEs)
* VGs
* LVs

lvs, vgs, pvs are handy commands to get sorter output than pvdisplay, vgdisplay, lvdisplay.
Also, most LV commands to extend or reduce LV sizes can deal with EXT4 file systems at the same time. Other file systems will need to be handled separately.

Clear as mud?

LVM provides so much flexibility that you'll learn to love it, I'm certain.  Do not allocate all the VG storage. Add it as needed, so you have a few weeks warning before the VG is totally used and need to either buy a larger disk or add more storage as PVs which can be used to extend the VG, making more room for LVs.

And when it is time to move to new storage, you'll be extremely happy to have LVM, since it makes moving to new storage trivial.

---

### Post by lbunch on 2019-05-03
The Fu,
thanks for the help.  I tried this at the command line, checking the case and spelling, etc:
sudo mount  /dev/mapper/ubuntu--vg-Storage  /storage ext4  0  2
This returned "mount: bad usage. . ."
I do have the /storage folder and it is empty.  It is not capitalized, and the mapper version of the volume is capitalized.  The Storage volume appears in lsblk as and "lvm" just like ubuntu-lv, the system partition.

I didn't mess with fstab since I should be able to mount it from the command line at least temporarily to check.  Right?
ideas?
Les.

---

### Post by rsteinmetz70112 on 2019-05-03
Typically you should only need this command to mount a file system:
```
$ sudo mount /dev/mapper/ubuntu-vgStorage /storage
```

Assuming there really is a device named /dev/mapper/ubuntu-vgStorage

If you need to add the filesystem type to the mount command you use the -t switch something like:

```
$ sudo mount -t ext4  /dev/mapper/ubuntu-vgStorage /storage
```

The line you would put in the /etc/fstab file would be something like:

```

#[Device]                       [Mount Point]       [File System Type]      [Options]       [Dump]       [Pass]
/dev/mapper/ubuntu-vgStorage    /storage            ext4                    defaults         0            2
```

---

### Post by lbunch on 2019-05-04
Thanks, guys, but I'm giving up.  Not something I like to do.  The inconsistencies or complexities of the LVM have worn me down.  Is it ubuntu--vg or ubuntu-vg?  If my prompt shows /storage# when I'm there, why doe "mounting point does not exist" when I try to mount to /storage?  
Thanks again for trying.

---

### Post by DuckHook on 2019-05-04
> **lbunch said:**
> Thanks, guys, but I'm giving up.  Not something I like to do.  The inconsistencies or complexities of the LVM have worn me down.  Is it ubuntu--vg or ubuntu-vg?  If my prompt shows /storage# when I'm there, why doe "mounting point does not exist" when I try to mount to /storage?  
Thanks again for trying.
I agree with your approach. I do have one partition/install on LVM and it's great for tinkering because I can revert to previous snapshots, but that's only one partition of three. The other two are standard and what I rely on for my base system. My advice would be to keep your base install as simple, standard and default as possible. Then do stuff like LVM on a separate partition after you have learned the ropes and are comfortable finding your way around in the CLI.

Good Luck and Happy Ubuntu'n!

---

### Post by TheFu on 2019-05-06
> **lbunch said:**
> Thanks, guys, but I'm giving up.  Not something I like to do.  The inconsistencies or complexities of the LVM have worn me down.  Is it ubuntu--vg or ubuntu-vg?  If my prompt shows /storage# when I'm there, why doe "mounting point does not exist" when I try to mount to /storage?  
Thanks again for trying.

Hopefully, you haven't moved on.

Storage devices make use of symbolic links.  If you understand those, then continue reading. If not, best to hop out to wikipedia and read a few paragraphs about them.  Symbolic links are handy for many things on Unix systems.  We use them all the time. They make directories or files located in convenience locations, even when they have to be located somewhere else, less convenient.

The full path to the device is on your computer. Storage devices are always under /dev/ somewhere.  
On my 16.04 system, LVM LVs are mapped under /dev/mapper.
```
/dev/mapper$ ls -alF
```
will show the /dev/mapper/{name} you want to use.  With those ls options, you'll see where the symbolic links actually point ... to the device-mapper "devices".

For non-LVM devices, you can find similar storage links under /dev/disk/
```

$ ls -F
by-id/  by-partlabel/  by-partuuid/  by-path/  by-uuid/
```

If you do a ```
find /dev/disk -ls
```
You'll see all the different possible device links by id, label, UUID and paths.  For more complex stores setups, I prefer to use by-path/ devices. Those don't change without physically modifying cables, cards, and disks.

Why do we use this level of indirection?  Wouldn't pointing at /dev/sda5 be much easier?  In the old days we did it that way, but as more storage, more partitions, became common, and different parts of the Linux boot sequence became parallelized, the different partitions and disks would be discovered in different order, so from boot to boot, sda , sdb, sdc, sde, sd ..... z order would change.  To solve that, someone decided that making UUIDs, which are tied to each partition, would be better.  This is the default for new installs of Linux and has been for about 15 yrs.  It solved the issue, but it is hardly intuitive.

The format for fstab is very different than the format for a CLI/shell mount command. You did check out the manpage for each, right?

---

### Post by TheFu on 2019-12-03
Came back to this .... 

Did you create a file system on the /dev/mapper/ubuntu-vgStorage  LV?  It isn't possible to mount storage that doesn't have a file system.  Use **sudo mkfs -t ext4 /dev/mapper/ubuntu-vgStorage**  for that.

Also, you'll want to confirm that /dev/mapper/ubuntu-vgStorage is the correct path to the LV device. On a VM server here, they are named in a consistent way:
```
/dev/mapper$ ls -F
control                         hadar--vg-lv--vpn09--1604@
hadar--vg-libvirt--lv@          hadar--vg-lv--xen41--1604@
hadar--vg-lv--blog44--1604@     hadar--vg-lv--zcs45--1604@
hadar--vg-lv--lubuntu11--1604@  hadar--vg-root@
hadar--vg-lv--spam3@            hadar--vg-swap_1@
hadar--vg-lv--spam61--1604@     hadar--vg-test--1804@
hadar--vg-lv--srv--1910@        vg--hadar-lv--backups@
```  Those are all symbolic links to "device mapper" devices which can change just like /dev/sdX device orders change.  But /dev/mapper/hadar--vg-lv--spam61--1604 will not change and will always point to the correct DM device.

---

