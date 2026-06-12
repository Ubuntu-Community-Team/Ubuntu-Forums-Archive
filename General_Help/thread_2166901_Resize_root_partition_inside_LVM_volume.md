---
title: "Resize root partition inside LVM volume"
date: 2013-08-11
forum: General Help
---

### Post by DrJohn999 on 2013-08-11
I created a KVM virtual machine in a 10-G logical volume using Vm-manager. I later expanded the logical volume to 30G. Now I want to resize the / partition that's inside the logical volume to occupy the new space. Here's what I have:
```
# lvs
  LV            VG   Attr     LSize   Pool Origin    Data%  Move Log Copy%  Convert
  vm-Dev        VG1  -wi-a---  30.00g
                                           
# fdisk -l /dev/VG1/vm-Dev

Disk /dev/VG1/vm-Dev: 32.2 GB, 32212254720 bytes
255 heads, 63 sectors/track, 3916 cylinders, total 62914560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009acb7

          Device Boot      Start         End      Blocks   Id  System
/dev/VG1/vm-Dev1   *        2048    18382847     9190400   83  Linux
/dev/VG1/vm-Dev2        18384894    20477951     1046529    5  Extended
/dev/VG1/vm-Dev5        18384896    20477951     1046528   82  Linux swap / Solaris

# 
```
The / partition (with ext4 filesystem) is mountable on the host with the correct offsets, but not directly as "/dev/VG1/vm-Dev1". Resize2fs run on the host system does not work directly on the logical volume, no doubt because the volume contains more than one partition. From within the running VM, I probably could manipulate the partition table to remove the swap partition and recreate it at the end of the volume, then resize the / partition to fill the remaining space, while mounted.
My question is whether there is a way to do this without starting up the vm, i.e. directly on the logical volume contents from the host?

---

### Post by DrJohn999 on 2013-08-17
Simple answer: connect the KVM VM's CDROM to a bootable iso image that can run gparted or any partition resizer. I used Virtual Machine Manager to connect to the 12.04.1 desktop iso. Boot from the iso and run as LiveCD, i.e. "Try Ubuntu". From there move the swap to the end of the drive space and resize the (not mounted) root partition (I used gparted in this case), shut down, disconnect the IDE CDROM device from the iso image and boot normally from the LVM image on the VirtIO Disk. Voilá!

---

