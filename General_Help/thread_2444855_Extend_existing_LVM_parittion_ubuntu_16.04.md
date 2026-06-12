---
title: "Extend existing LVM parittion ubuntu 16.04"
date: 2020-06-05
forum: General Help
---

### Post by Drenriza on 2020-06-05
Hi all, i have a Ubuntu 16.04 server that have 10 GB for it's HDD.
Now i would like to extend / expand this to 20 GB, in my VM setup i have expanded my existing HDD from 10 to 20 GB and i would like Ubuntu
to use this new available space.

From what i can read i can extend my LVM volume and use the available space with the commands
```
$ lvm
lvm> lvextend -l +100%FREE /dev/{myMachineName}-vg/root
lvm> exit
resize2fs /dev/{myMachineName}-vg/root
```

But before i can do the above i need to extend my existing /dev/sda partition to into the new available space.

My question is: With fdisk how can i extend the already existing /dev/sda partition when the partition system setup is as follows? (default installation)
> Device     Boot   Start      End  Sectors  Size Id Type
/dev/sda1  *       2048  1499135  1497088  731M 83 Linux
/dev/sda2       1501182 20969471 19468290  9.3G  5 Extended
/dev/sda5       1501184 20969471 19468288  9.3G 8e Linux LVM

I have found a guide that explains how to extend the ubuntu filesystem into a bigger partition in a slightly different scenario
[https://askubuntu.com/questions/116351/increase-partition-size-on-which-ubuntu-is-installed](https://askubuntu.com/questions/116351/increase-partition-size-on-which-ubuntu-is-installed)
Is that the way to go? Would i just need to re-create all the partitions again from the same starting point to the end of the disk as the guide suggests, minus the boot disk that needs to be exactly as it is.

I have never extended a virtual machines LVM disk, any advice / suggestions are most welcome.

Thanks in advance
Best regards

---

### Post by Dennis N on 2020-06-05
I used the procedure described here:
[Resize a qcow2 image with virt-resize]("https://fatmin.com/2016/12/20/how-to-resize-a-qcow2-image-and-filesystem-with-virt-resize/")
(It looks like you may have only done the first step of resizing the virtual disk since the partition is stlll <10G.)

---

### Post by TheFu on 2020-06-05
There's the physical parts and the logical parts.  Let's break down everything to make it clearer.  it is unclear how the storage from the VM hypervisor is presented to the VM.

The VM part where you made it bigger is like swapping the disk for a larger one AND having all the bits cloned into the large physical disk.

Does the VM see the larger storage inside or not?  

if not, there is either a step missing from the hypervisor level or the vHDD inside the VM needs to be forced to re-read the vHDD parameters.  

From inside, the disk looks to have 2 primary partitions
a) boot
b) extended partition
Then inside the extended partition is a logical partition with the LVM stuff.  That's a PV, VG, and at least 1 LV, but you haven't posted that data, so we don't actually know.

Anyways, the LV can't be changed inside without the VG, PV, logical partition and extended partition being changed first - in reverse order.  Changing the partitions means they cannot be in-use - i.e. mounted.  That means you'll want to add a Try Ubuntu iso to the CDROM and boot from that, choose "try ubuntu", install the LVM2 and gparted packages and get to work in the correct order. Doing the LVM stuff inside the Try Ubuntu environment is optional. Doing the partition stuff is not.

However, with using LVM, there are some other methods to increase available storage that are far easier.  Rather than increasing the vHDD size, another vHDD could have been added by the hypervisor. Reboot so the guest VM sees that new vHDD, then you'd create a new PV on that new disk, add the new PV to the existing VG and use lvextend (use the -r option to resize the filesystem too) for the current LV - Bob's your uncle.  All the LVM work can be done while the system is running.

There are a few other techniques if Linux LVM is running on the hypervisor where the storage can automatically increase taking available space from a thin provisioned pool. But that ship has probably already gone.

---

### Post by TheFu on 2020-06-05
if lvextend or lvresize is used without the -r option, then you have to remember to resize the file system.  Easier to just use the option and have 1 command handle it.  Check whether it works for file systems other than ext4.  i don't know  if it does or not.

---

### Post by kneutron on 2020-06-05
--I've done this several times.  First, MAKE A BACKUP. Snapshot your virtual machine before resizing, clone it, or with the VM powered off make a copy of its disk file on the host.

--After resizing the disk on the host**, you may need to reboot the VM for it to "see" the change.  Ubuntu is better than Centos/Red hat at this, you may get lucky.

** You can do "live" disk resizes on vsphere and IIRC on vmware workstation, maybe notsomuch on Virtualbox

See:
[http://sirlagz.net/2016/01/20/live-resizing-lvm-on-linux/](http://sirlagz.net/2016/01/20/live-resizing-lvm-on-linux/)

PROTIP: when you resize the LVM: use ' lvextend -r -L +99G lvmname-lvmpart ' and use the appropriate number of GB.  It will eliminate the separate "resize filesystem" step in that article.

---

### Post by TheFu on 2020-06-05
Why are people assuming the hypervisor is using file-based storage? The OP never said that.

I'm using KVM as the hypervisor.

Anyways, I have a 20.04 VM system running on a 16.04 server that uses LVM to provide storage to the VM-guest. Here's exactly the situation and how I'll expand the storage in just a few commands:

Current situation, **inside the guest:**
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   12G   **11G**  188M  99% /
/dev/mapper/vgubuntu--mate-home ext4   12G  5.9G  5.4G  53% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
```
It be out of storage on /. 12G  with 11G used.  Ouch!  I knew my 30G virtual-HDD was going to be tight, but the prior system was 20G with 10G free on 16.04.  Ah ... 2.5G of snaps. There's one bloated difference.  I also set a 4.1G swap.
```
$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin 
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  root   vgubuntu-mate -wi-ao---- 12.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g  
```
Ok, because I use LVM, I don't need to resize vda.  I'll just add vdb using the hypervisor.

**From the hypervisor:**
```
$ sudo lvs
  LV                VG       Attr       LSize    
  lv-regulus        hadar-vg -wi-ao----  30.00g   
```   
```
  $ sudo vgs
  VG       #PV #LV #SN Attr   VSize   VFree 
  hadar-vg   1  13   0 wz--n- 476.22g 42.44g
  vg-hadar   1   1   0 wz--n- 465.76g 36.00m

```
There are other LVs for other VMs and for local OS storage. hadar-vg has some free storage. 10G more for the new vHDD.

**From the hypvisor**, I added 10G more while the system was running. This is like adding a hot-swap HDD without any partitions, no partition table, just slapped it into the VM. This is from the hypervisor still:
```
$ sudo lvs
  LV                VG       Attr       LSize   Pool 
  lv-regulus        hadar-vg -wi-ao----  30.00g                                                    
  **lv-regulus-2**      hadar-vg -wi-ao----  **10.00g**      
```

**Inside the guest-VM, regulus,** it showed up as:
```
$ sudo fdisk -l /dev/vdb
Disk /dev/vdb: 10 GiB, 10737418240 bytes, 20971520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```
Sweet!  
Create a partition table, primary partition, set the partition type to Linux LVM inside vdb, then check it:
```
Disk /dev/vdb: 10 GiB, 10737418240 bytes, 20971520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: **gpt**
Disk identifier: FADD8143-17B4-E446-B328-34BCE660B93C

Device     Start      End  Sectors Size Type
/dev/vdb1   2048 20971486 20969439  10G Linux LVM
```

That's it for partitioning. The system was running the entire time.
**vgextend** is our friend to add the new vdb1 partition to our existing VG, vgubuntu-mate 
```
 $ sudo vgextend vgubuntu-mate  /dev/vdb1
  Volume group "vgubuntu-mate" successfully extended

$ sudo vgs
  VG            #PV #LV #SN Attr   VSize  VFree 
  vgubuntu-mate   2   3   0 wz--n- 39.49g 11.39g
```
Finally, let's extend the LV nearly out of space by 5G:
```
$ sudo lvextend -r --size +5G  /dev/vgubuntu-mate/root  
  Size of logical volume vgubuntu-mate/root changed from 12.00 GiB (3072 extents) to 17.00 GiB (4352 extents).
  Logical volume vgubuntu-mate/root successfully resized.
resize2fs 1.45.5 (07-Jan-2020)
Filesystem at /dev/mapper/vgubuntu--mate-root is mounted on /; on-line resizing required
old_desc_blocks = 2, new_desc_blocks = 3
The filesystem on /dev/mapper/vgubuntu--mate-root is now 4456448 (4k) blocks long.
```

and checking the df:
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   **17G**   11G  4.9G  69% /
/dev/mapper/vgubuntu--mate-home ext4   12G  5.9G  5.4G  53% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
```
17G  with 11G used.

And the lsblka:
```
$ lsblk
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sr0                       1024M rom              
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home
vdb                         10G disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9492;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
```

Why did I add 10G more storage to the VG, but only add 5G more to the LV?  Hummmm.

And just for fun, here's the uptime inside the VM-guest, regulus:
```
$ uptime
 19:01:43 up 6 days, 11:25,  2 users,  load average: 0.28, 0.18, 0.10
```
Zero downtime for this process.
It would take under 5 minutes if I wasn't posting here as I did it and checking manpages carefully.  Knowing what was possible means it isn't hard to find a path to a solution.

Ok, the only reason I did it this way was because all the storage in this physical system is on a single SSD, so there wouldn't be any redundancy problem by adding another virtual-HDD to an existing system in this way. I could have disabled the swap LV, stolen that 4.1G for the "root" LV, then added a different virtual-disk for the swap too.  I might do that still, just because it will seem cleaner.

And if this really bothers me, I could create a new vHDD and use pvmove to relocate all the current PVs onto the new storage as a way to consolidate it.  LVM provides, options.  So does using virtual machines.  But only if the VMs don't get full.  Having some free storage in the VG means we can create snapshots before doing backups, take the non-changing snapshot for a backup, then delete the snapshot when we finish.

Bob's my uncle too. ;)

---

### Post by kneutron on 2020-06-06
> [COLOR=#000000]Why are people assuming the hypervisor is using file-based storage? The OP never said that

--Doesn't really matter?  For the people who come across this link in the future that do, the advice still applies.  

--I've used the link I provided in an Enterprise Vsphere environment where they discourage adding disk sdb (or sdc, because sdb is swap) because the higher-ups want the VMs to be mostly the same - and if you already have 4 primary partitions with LVM on sda because the Red Hat installer was $stupid, pretty much the only thing you can do is expand the last one.[/COLOR]

---

### Post by TheFu on 2020-06-07
> **kneutron said:**
> Why are people assuming the hypervisor is using file-based storage? The OP never said that

--Doesn't really matter?  For the people who come across this link in the future that do, the advice still applies.  

--I've used the link I provided in an Enterprise Vsphere environment where they discourage adding disk sdb (or sdc, because sdb is swap) because the higher-ups want the VMs to be mostly the same - and if you already have 4 primary partitions with LVM on sda because the Red Hat installer was $stupid, pretty much the only thing you can do is expand the last one.

Agreed.  In corporate environments, being consistent is extremely important and often prevents tired admins at 3am Sunday morning from making mistakes during major upgrades.

---

### Post by Drenriza on 2020-06-08
Hi all!

Thanks for all the great replies!

To clear some of the questions asked earlier.

I extended the vHDD from 10 to 20GB on my VM system _**AND**_
Ubuntu does see the new 10GB available space with fdisk /dev/sda and F option.

I understand that there is a "physical" part and a logical part to using LVM and extending the environment.
1. Extend or add the "physical" disk
2. Extend the logical LVM environment

I am by no means a LVM expert and i have never extended the LVM environment before in Ubuntu.
So for the physical part i went in with fdisk

```
sudo fdisk /dev/sda
```
And deleted partition 2 and 5

I than re-created partition 2 with the same start (1501182) sector and extended the end sector to the end.
But when i wanted to re-create partition 5 with the start sector of 1501184 fdisk said the value was out of range and i could only create from 1503232 as the first available sector.

I have found out that i can "force" start sectors as i want with parted, but that system seems alot more risky because it write changes immediately to the disk, as wher in fdisk i can just q option out and dont write anything to the system.

Question. Does it make any difference that the Linux LVM 8e partition starts from 1503232 instead of 1501184 as it was originally created?
Why are there two partitions that seems to do the same thing?
Would i lose data if i started from 1503232 instead of 1501184 (curious)?
Is there a way to force fdisk to start at a given sector and get around the "value out of range" error?


@TheFu
> However, with using LVM, there are some other methods to increase  available storage that are far easier.  Rather than increasing the vHDD  size, another vHDD could have been added by the hypervisor. 

I have read that a more common approach is to create a new vHDD instead of increasing the existing one, partition the disk and add this to the LVM volume.
This approach is alot like how ZFS does it (in my opinion), and i guess i could have done it like this but that wasnt my first thought. In my head i was like i needed to extend the existing vHDD and add the space instead of creating a new one.

Are there any advantage from the Hypervisor or from the VM to extend existing vHDD's versus adding new ones?
Besides it seems more complicated from Ubuntu to extend into new available space than to add new space.

> Why are people assuming the hypervisor is using file-based storage? The OP never said that.
I have no idea :)

---

### Post by TheFu on 2020-06-08
Why delete partitions?  Doesn't that seem bad to anyone else too?

Logical partitions and Extended Primary Partitions are different things, but you need to understand them if your setup uses them.  Wikipedia has articles on each.  in short, they are a work-around for DOS partition table limitations.

Not sure that adding another vHDD is more common, but if you have LVM why not make your life easier and use the capabilities?  Without LVM, you wouldn't have any choice - partitions have to be contiguous.  LVs do not.

if i was where you are now, i'd put everything back the way it was and start over.   Or just create a new vHDD that is bigger and restore my backups into that larger storage area.

is there a reason you didn't just hook up a Try Ubuntu desktop iso to the VM, boot that and use gparted to  ... let me see what i wrote ....
> Then inside the **extended partition** is a **logical partition** with the LVM stuff. That's a PV, VG, and at least 1 LV, but you haven't posted that data, so we don't actually know.
There's an order required in these steps.
[LIST=1]
[*]increase the vHDD using hypervisor tools
[*]Boot from Try Ubuntu desktop, run **gparted**; changing partitions can't be done when mounted
[*]increase Extended Partition size 
[*]increase Logical Partition size  # that's it for gparted.
[*]**sudo vgchange -ay** # so the LVM parts are seen and active, but not mounted
[*]i think the PV should see the size change automatically.  Check w/  **pvs**
[*]Extended the VG ... somehow  ...  vgconvert/**vgextend**.  Check w/ **vgs**
[*]increase the LV **lvextend**  and remember to use the **-r** switch so the file system is extended too.  Check w/ **lvs**
[*]Shutdown, disconnect iso and reboot into the normal OS
[/LIST]
That should be it, but uuids may break the fstab. For LVM mounts, i don't use uuids in the fstab.

Changing the order above makes no sense to me.

---

