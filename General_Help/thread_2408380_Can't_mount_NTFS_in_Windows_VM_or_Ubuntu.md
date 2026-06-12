---
title: "Can't mount NTFS in Windows VM or Ubuntu"
date: 2018-12-17
forum: General Help
---

### Post by zaurian on 2018-12-17
I'm pulling my hair out here. I've been working on this for two weeks and have had nothing but one problem after another.  I really want to be done with Windows VMware Workstation and would love nothing more than to make Linux my baremetal OS, but frankly I'm getting close to giving up and this is my hail mary.  I'll spare you of too much irrelevant history and detail, but here is where I am at now...

AMD Threadripper 1950X. 128G RAM. 2 x 1Tb NVMe drives.

I have Windows 10 running in Qemu. I am successfully passing through my GeForce 1080Ti card, as well as a USB controller. I have Looking Glass installed so I can view the VM while at the Ubuntu desktop. My primary boot disk is in Qcow2 format. I'm booting OVFM UEFI. I want a second disk drive set up to work as fast as possible for gaming. I created a partition for this purpose on one of the NVMe drives (nvme0n1p4).  Here is what happened next:

- If I format NTFS in Linux, Windows see's an un-formatted disk
- If I then format in Windows, it works in Windows, but Linux still sees the original format it did; marker files placed there in Linux are still there. I can modify the partition in either OS and only that OS sees the changes. Obviously this is corruption waiting to happen, so I added the partition as noauto in /etc/fstab and just resigned myself to not being able to mount the partition in Linux; for use in Windows only.
- I originally was able to mount the partition by /dev/disk/by-uuid/xxx ... I installed many programs in the guest using the partition as a data drive. I rebooted numerous times, both the guest and the host, and everything seemed to work fine... for two days.

Now, I am unable to mount the partition.  In Ubuntu, the UUID has disappeared; Disk Manager now reports that the Partition Type is "Basic Data" and that the Contents are "Unknown".  Because the UUID has disappeared from Ubuntu, I can't mount the disk that way any longer for the VM.  So, I edited the VM and I'm now mounting this way:

```
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none'/>
      <source dev='/dev/disk/by-path/pci-0000:41:00.0-nvme-1-part4'/>
      <target dev='vdb' bus='sata'/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
```

Since I was originally mounting by-uuid, should I expect the disk to still work in Windows?  Either way, it doesn't.  It now see's an un-formated disk again. Of course I can re-format and start over, but what's the point if I don't understand what went wrong the first time. Ideally, I'd like to be able to mount an NTFS partition that is visible by both Linux and Windows, and I've tried much more than what I've stated here, without success.

It would be great if I could recover the NTFS partition in Windows, even just if to recover the two-days worth of data I installed.  It's interesting that Disk Manager shows the partition as type 'Basic Data'  but that parted and fdisk see it as "microsoft basic data"  or NTFS.  Here is the output of several relevant commands (cropped out other disks):

```

steve@Threadripper-U3:/dev$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme1n1     259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme1n1p1 259:6    0   512M  0 part /boot/efi
&#9500;&#9472;nvme1n1p2 259:7    0  59.6G  0 part /
&#9500;&#9472;nvme1n1p3 259:8    0 405.8G  0 part /media/steve/NVMe1n1p3-Ext4
&#9492;&#9472;nvme1n1p4 259:9    0 465.7G  0 part 

steve@Threadripper-U3:/dev$ blkid
/dev/nvme1n1p1: UUID="DAC1-6625" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="a9fac4cf-31e6-45f0-8868-2571b4d2991c"
/dev/nvme1n1p2: UUID="ae0d0f65-236a-4e9e-9c45-5fbe47b4ff53" TYPE="ext4" PARTUUID="f8052080-068d-4d69-97d7-3200afe32865"
/dev/nvme1n1p3: LABEL="NVMe0n1p3-Ext4" UUID="d8ad7d54-0c61-4d7c-9b27-8e66ee56f583" TYPE="ext4" PARTUUID="b7ed2eea-474b-4a24-a0ad-30dbf6638b22"

steve@Threadripper-U3:/dev$ blkid -c /dev/null -o list
device                                                 fs_type         label            mount point                                                UUID
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/nvme1n1                                                                                (not mounted)                                                  
/dev/nvme1n1p1                                                                              /boot/efi                                                      
/dev/nvme1n1p2                                                                              /                                                              
/dev/nvme1n1p3                                                                              /media/steve/NVMe1n1p3-Ext4                                    
/dev/nvme1n1p4                                                                              (not mounted)  

steve@Threadripper-U3:/dev$ sudo parted /dev/nvme1n1p4 unit s print
Model: NVMe Device (nvme)
Disk /dev/nvme1n1p4: 976562176s
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 
Number  Start  End         Size        File system  Flags
 1      0s     976562175s  976562176s  ntfs

steve@Threadripper-U3:/dev$ sudo parted -l
Model: Samsung SSD 960 EVO 1TB (nvme)
Disk /dev/nvme1n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 
Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   64.5GB  64.0GB  ext4
 3      64.5GB  500GB   436GB   ext4
 4      500GB   1000GB  500GB   ntfs                               msftdata


steve@Threadripper-U3:/dev$ sudo fdisk -lu
Disk /dev/nvme1n1: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 028610DE-F907-4AA7-994D-1A6B29820DBF

Device             Start        End   Sectors   Size Type
/dev/nvme1n1p1      2048    1050623   1048576   512M EFI System
/dev/nvme1n1p2   1050624  126052351 125001728  59.6G Linux filesystem
/dev/nvme1n1p3 126052352  976961535 850909184 405.8G Linux filesystem
/dev/nvme1n1p4 976961536 1953523711 976562176 465.7G Microsoft basic data

steve@Threadripper-U3:/dev$ sudo fdisk -l /dev/nvme1n1p4
Disk /dev/nvme1n1p4: 465.7 GiB, 499999834112 bytes, 976562176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

```

Does anyone have any ideas where I may be going wrong or what I might try in order to get this to work?  At this point, my next step is to ditch the idea of raw disk access and just create a second Qcow2 for my data drive in Windows. But it sure would be nice to understand why this doesn't work.

Thank you to anyone who may be able to help me troubleshoot or provide any insight in to what I may be misunderstanding here.

Steve

---

### Post by TheFu on 2018-12-18
There is a misunderstanding here.  The easiest way to explain it is that you have 2 choices.
a) pass through a block device to the guest OS for exclusive use. There are a few ways to do this. qcow2, PCI passthru, LVM passthru
or
b) setup a networked file sharing solution. Samba, CIFS, or the method provided by a hypervisor.

BTW, I hope you aren't just using QEMU, but are using KVM which leverages the amd-v HW extensions for virtualization context switching. QEMU is much, much, much slower than KVM.

If you use the "a" method, you can use the "b" method from which ever OS has the exclusive use of the block device.  You can NEVER, EVER, move that block device access back to the hostOS, but if you power off 1 guest, it should be recognized by another guest running the same guest OS.  Windows to Windows. Linux to Linux.

Never allow/force 2 OSes to access a single block storage device concurrently.  That is begging for corruption.  Each OS assumes it has 100% control over the storage device and does caching to speed up access.  Also, Windows uses some techniques whereby it doesn't actually close the file system between booting, leaving the disk "open" - begging for more corruption.  You can disable fastboot (or whatever they decided to call it this year), which should help. Regardless, only 1 OS should access any block device at a time.

Clear as mud?

---

### Post by zaurian on 2018-12-18
Thank you for your reply!


Yes, I am using KVM and taking advantage of AMD-Vi; this is also required for the PCI passthrough that I'm doing for the video card and the USB bus.


I realize that I cannot have both Linux and Windows have access to the same partition at any given time. What I was hoping for is the ability to mount the NTFS partition within Linux when the VM is powered down, thereby being able to read/write data without requiring the VM to be powered on or taking the performance hit of CIFS/Samba.  I thought that passing a partition of type 'block' and referencing the /dev would allow me to do this. Perhaps that is not the case.


I know that I could create another qcow2 file for my data drive in the Windows VM, but I'm hoping for better performance than that. I also believe that I can't mount a qcow2 image directly in Linux without using virsh, right?


So what is the best way to accomplish what I'm trying to do?  Are you saying that there is no way to pass an NTFS partition to a VM and still have that partition available to Linux when the VM is powered down? That doesn't seem right.  What is it about my method detailed above, where I pass the block device by-path or by-uuid (when it was working), that is unstable or not recommended?


I have no real experience with LVM; I'll take a look at this... cursory overview tells me maybe it's the right way to do a storage pool, but I need to do my research here...

---

### Post by TheFu on 2018-12-18
Can't answer all the questions. Outside my knowledge.

You can access qcow2 storage from the host using a loop mount, but it sounds like using LVM passthru is more what you need for VM storage.

Have you considered using kpartx to get the partition mapping?  [https://manpages.ubuntu.com/manpages/bionic/man8/kpartx.8.html](https://manpages.ubuntu.com/manpages/bionic/man8/kpartx.8.html)

As for accessing storage controlled by Windows inside a VM, I'd use a network share over a virtio network device. That should provide enough performance. It does for me, but I don't have any SSD/nvme devices.  I'm only running Windows media center inside a KVM VM.  I don't game.

---

### Post by zaurian on 2018-12-18
Thank you for bringing my attention to LVM and kpartx.  I am pretty new to this and it's been quite the adventure, but now I have created volumes using LVM and installed VirtIO drivers in my Windows VM, which supposedly improves performance over IDE or SATA.  So far so good.  While I don't think the performance will match raw performance, I think this is a safer and more manageable way to go.  I gave up on trying to recover my earlier NTFS partition; hopefully using LVM this will be the last time I have to re-install everything!  Much appreciated.

Cheers!

---

