---
title: "Please help with increasing swap partition on LVM on LUKS"
date: 2023-06-08
forum: General Help
---

### Post by Paddy Landau on 2023-06-08
I have a swap partition of 2 GB. However, I'm working with very large images, and sometimes both the swap and RAM fill up, so the app in question crashes.

Thus, I need to shrink my root partition and increase my swap partition.

I know how to do this with a normal set of partitions — I use [GParted]("https://gparted.org/"), easy to do.

The problem is that these partitions are on LVM, which is in turn on a LUKS partition, and I don't know how to safely manipulate them. GParted doesn't work in this instance — it seems unable to deal with virtual LVM partitions. Gnome Disks doesn't give an option to resize.

The system was installed using the standard Ubuntu installation process with full-disk encryption. My current setup is:

[LIST]
[*]Partition 1: EFI System Partition (FAT)
[*]Partition 2: Boot (ext4)
[*]Partition 3: LUKS, which contains:
[LIST]
[*]LVM, which contains:
[LIST]
[*]Root (ext4) — /dev/vgubuntu/root
[*]Swap — /dev/vgubuntu/swap_1
[/LIST]
[/LIST]
[/LIST]
I've tried looking up how to do this, and I'm hopelessly confused.

So, how do I go about shrinking Root and then expanding Swap, please? I can boot from a Live USB and unlock the LUKS partition, but what then?

Thank you

---

### Post by MAFoElffen on 2023-06-08
LUKS is only a factor, as it is in the outer layer, in that in dealing with it offline, you will need to onlock the LUKS container. Before doing anything else.  

After that, the Logical plan is to shrink the root LV  then grow the swap LV. Since it is a root partition... Do it offline from a LiveUSB... That is done in steps of resizing the filesystem, and the LV size. Before, those were separate steps. Now can be done at the same time, using an added option.

Do you need instructions? And in how much detail? (At what skill level is the target?)

What would help for that is to please post the results of this within CODE Tags:
```

sudo lsblk -o name,mountpoint,fstype,size,type,fsavail,fsuse% |  grep -v 'loop'
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
ls -l /dev/mapper/

```
Or run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info"), but use the '--details' option when you start it to include details filesystem information (for your LVM2)... And post the URL of where the report uploads to a pastebin.

---

### Post by Paddy Landau on 2023-06-09
Thank you for your reply.
> **MAFoElffen said:**
> Do you need instructions? And in how much detail? (At what skill level is the target?)
I fully understand the concepts of both LUKS and LVM, and I'm very comfortable with the terminal. I just can't get my head around which commands to use for LVM!


Here are the results from your commands.
```
$ [COLOR=#0000cd]sudo lsblk -o name,mountpoint,fstype,size,type,fsavail,fsuse% |  grep -v 'loop'[/COLOR]
NAME                  MOUNTPOINT                         FSTYPE        SIZE TYPE  FSAVAIL FSUSE%
nvme0n1                                                              476.9G disk
&#9500;&#9472;nvme0n1p1           /boot/efi                          vfat          512M part   447.9M    12%
&#9500;&#9472;nvme0n1p2           /boot                              ext4          1.7G part     1.2G    17%
&#9492;&#9472;nvme0n1p3                                              crypto_LUKS 474.8G part
  &#9492;&#9472;nvme0n1p3_crypt                                      LVM2_member 474.8G crypt
    &#9500;&#9472;vgubuntu-root   /                                  ext4        472.8G lvm    336.9G    22%
    &#9492;&#9472;vgubuntu-swap_1 [SWAP]                             swap          1.9G lvm
```
```
$ [COLOR=#0000cd]sudo pvdisplay[/COLOR]
  --- Physical volume ---
  PV Name               /dev/mapper/nvme0n1p3_crypt
  VG Name               vgubuntu
  PV Size               474.75 GiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              121536
  Free PE               0
  Allocated PE          121536
  PV UUID               1KC1qN-dEiE-UR4H-vjgK-ctEa-s5Qd-gXQ1cj
```
```
$ [COLOR=#0000cd]sudo vgdisplay[/COLOR]
  --- Volume group ---
  VG Name               vgubuntu
  System ID            
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               474.75 GiB
  PE Size               4.00 MiB
  Total PE              121536
  Alloc PE / Size       121536 / 474.75 GiB
  Free  PE / Size       0 / 0  
  VG UUID               otQBwZ-1DX9-R860-tnRL-dvtu-ixhz-3VeSHu
```
```
$ [COLOR=#0000cd]sudo lvdisplay
[/COLOR]
  --- Logical volume ---
  LV Path                /dev/vgubuntu/root
  LV Name                root
  VG Name                vgubuntu
  LV UUID                PHWpL2-Iy7V-Ha7g-In5Q-oOP9-lrk4-XcvDxf
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2022-08-28 10:38:40 +0100
  LV Status              available
  # open                 1
  LV Size                <472.84 GiB
  Current LE             121047
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/vgubuntu/swap_1
  LV Name                swap_1
  VG Name                vgubuntu
  LV UUID                cLmJSN-SqtY-xBpB-b1Qi-DcQI-1Zfk-KKBwqp
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2022-08-28 10:38:41 +0100
  LV Status              available
  # open                 2
  LV Size                1.91 GiB
  Current LE             489
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2
```
```
$ [COLOR=#0000cd]ls -l /dev/mapper/[/COLOR]
total 0
crw------- 1 root root 10, 236 Jun  9 08:36 control
lrwxrwxrwx 1 root root       7 Jun  9 08:36 nvme0n1p3_crypt -> ../dm-0
lrwxrwxrwx 1 root root       7 Jun  9 08:36 vgubuntu-root -> ../dm-1
lrwxrwxrwx 1 root root       7 Jun  9 08:36 vgubuntu-swap_1 -> ../dm-2
```

---

### Post by Dennis N on 2023-06-09
Here's is an actual example I saved in my notes where I reduced the root LV by 3000 extents. You can adapt this for your case.

```
dmn@Sydney:~$ sudo lvreduce --resizefs --extents -3000 /dev/os_vg/mint_xfce
fsck from util-linux 2.31.1
Mint-XFCE: 343994/1753088 files (0.4% non-contiguous), 2228585/7004160 blocks
resize2fs 1.44.1 (24-Mar-2018)
Resizing the filesystem on /dev/mapper/os_vg-mint_xfce to 3932160 (4k) blocks.
The filesystem on /dev/mapper/os_vg-mint_xfce is now 3932160 (4k) blocks long.

  Size of logical volume os_vg/mint_xfce changed from <26.72 GiB (6840 extents) to 15.00 GiB (3840 extents).
  Logical volume os_vg/mint_xfce successfully resized.
```

Making an LV larger would use lvextend.

---

### Post by Paddy Landau on 2023-06-09
> **Dennis N said:**
> Here's is an actual example&#8230;
Fantastic, thank you! I have no idea how big an extent is, so I'll use size instead. (**EDIT:** I think that an extent is 4MB.) I've been reading the man pages, and this is what I think will work:
```
sudo lvreduce --resizefs --size -4G /dev/vgubuntu/root     # Reduce Root by 4 Gb
sudo lvextend --resizefs --extents=+100%FREE /dev/vgubuntu/swap_1   # Increase swap by 4 Gb
```
(Edited to use [FONT=courier new]+100%FREE[/FONT].)
Do you agree?

Another question: I don't understand why one might use [FONT=courier new]+[/FONT] with lvreduce or [FONT=courier new]-[/FONT] with lvextend. For example, what would these mean?
```
sudo lvreduce --size +4G ...
sudo lvextend --size -4G ...
```
I also see that [FONT=courier new]--autobackup=y[/FONT] is strongly advised, and that I can use [FONT=courier new]--test[/FONT] for a test run.

---

### Post by Dennis N on 2023-06-09
For reference:

1 GiB = 250 extents
4 GiB = 1000 extents

The commands look ok to me. You have plenty of free space in the LV for the reduction to be successful. 

As to the + with lvreduce, I don't know what it would actually do. Without any - sign the reduction should reduce the file system to the size you specify.

---

### Post by Paddy Landau on 2023-06-09
> **Dennis N said:**
> For reference:

1 GiB = 250 extents
4 GiB = 1000 extents

The commands look ok to me. You have plenty of free space in the LV for the reduction to be successful. 

As to the + with lvreduce, I don't know what it would actually do. Without any - sign the reduction should reduce the file system to the size you specify.
Thank you. If I get some time, I'll try using + with lvreduce or - with lvextend in a VM (for safety). If I do this, I'll let you know the results.

---

### Post by TheFu on 2023-06-09
```
$ sudo lsblk -o name,mountpoint,fstype,size,type,fsavail,fsuse% |  grep -v 'loop'
NAME                  MOUNTPOINT                         FSTYPE        SIZE TYPE  FSAVAIL FSUSE%
nvme0n1                                                              476.9G disk
&#9500;&#9472;nvme0n1p1           /boot/efi                          vfat          512M part   447.9M    12%
&#9500;&#9472;nvme0n1p2           /boot                              ext4          1.7G part     1.2G    17%
&#9492;&#9472;nvme0n1p3                                              crypto_LUKS 474.8G part
  &#9492;&#9472;nvme0n1p3_crypt                                      LVM2_member 474.8G crypt
    &#9500;&#9472;vgubuntu-root   /                                  ext4        472.8G lvm    336.9G    22%
    &#9492;&#9472;vgubuntu-swap_1 [SWAP]                             swap          1.9G lvm
```

l;vreduce can go badly, so be certain you have a backup of everything you don't want to lose first.  In general, immediately post-install, I reduce / to be 25G-35G, since that's all the space an OS should need.

Then I add LVs for /tmp, /var, and /home sized small.  Growing an LV is trivial if it has an ext4 file system. Reducing them is a pain.  Additionally, I think they need to be umounted for the reduce to work.  For /, that would mean you'll need an ISO boot and run inside a Try Ubuntu environment.

I've never lvextend'ed swap.  Don't know if that will work since LVM only supports the ext4 file system for resize. Worst case, turn off the swap (swapoff), lvextend the device, then use mkswap on the newly larger LV, then use **swapon**.  I'm a little worried that extending the swap would end up with non-contiguous swap. While it will work, it isn't ideal on spinning HDDs, so I usually, disable the swap, delete the LV, create a new swap LV of the size I want (getting it in a single, contiguous chunk), then re-enable the swap. If I changed the LV name, I'd fix /etc/fstab with the new name using the /dev/{vgname}/{lvname} link.  I find those are the easiest to understand in the fstab and provides the most information for the least typing.

Always, always, use the smallest LVs you can, sized for specific needs over the next 3 months with LVs that contain anything except swap.  Increasing an LV with ext4 is trivial, requires ZERO downtime and is risk free (pretty much).

Also, I prefer the shorter LVM overview commands, **pvs, vgs, lvs**.  They get to the point with much less text input and output. There are times when we need to see all the details of the extremely verbose *vdisplay commands, but that only happens about once a decade for me. **sudo lvs** almost always tells me everything I need to know.

---

### Post by Paddy Landau on 2023-06-09
> **TheFu said:**
> … be certain you have a backup of everything
I shall do so, thanks for the warning.
> **TheFu said:**
> … I reduce / to be 25G-35G, since that's all the space an OS should need. Then I add LVs for /tmp, /var, and /home sized small…
I'm a single user on this computer, so I use just the one partition for everything. That makes the space more efficient, as I don't have to have spare space on several partitions.
> **TheFu said:**
> I've never lvextend'ed swap…
Worst case scenario, I'll have to reformat swap. That should be easy. I'll do this from a Live USB, so I don't have to worry about anything being mounted.
> **TheFu said:**
> … it isn't ideal on spinning HDDs
Mine's an SSD, so that'll be OK.

> **TheFu said:**
> I prefer the shorter LVM overview commands…
I think that for someone like you who knows what you're doing, that makes sense. For me, the longer commands are better because it helps me to understand what I'm doing!

Thank you for your feedback, appreciated as always.

---

### Post by Paddy Landau on 2023-06-09
Update:

I tested this all in a VM, and everything worked perfectly. As @TheFu suspected, you can't use --resizefs with swap, but mkswap after resizing did the trick.

Using + with lvreduce or - with lvextend are, fortunately, rejected with an error message.

---

### Post by TheFu on 2023-06-09
> **Paddy Landau said:**
> Update:

I tested this all in a VM, and everything worked perfectly. As @TheFu suspected, you can't use --resizefs with swap, but mkswap after resizing did the trick.

Using + with lvreduce or - with lvextend are, fortunately, rejected with an error message.

I see the double-check on bigger/smaller being a good thing.
LVM is kinda cool.  Too bad so many people avoid using it.  Did you vastly resize down the "root".  /, LV to have more flexibility in the future?  After all, using snapshots as part of pre-upgrade and nightly backups requires space.  Those 2 capabilities are very handy.  Creating a snapshot pre-weekly patching has saved me a few times, though it isn't as nice as ZFS snapshots.

Don't overestimate my knowledge of LVM.  I don't always know what I'm doing either.  That's why VMs are useful. Try it out there first.  BTW, VMs that use LVs directly as raw disks are very nice, if you aren't doing that already.

---

### Post by #&amp;thj^% on 2023-06-09
> **TheFu said:**
> BTW, VMs that use LVs directly as raw disks are very nice, if you aren't doing that already.

+1 indeed they are. And if others are not.....Why?

---

### Post by Quarkrad on 2023-06-09
A bit off topic but could you expand a bit on this **VMs that use LVs directly as raw disks**?  To date I have created a lv, formatted it as ext4 and then created the vm.

---

### Post by Paddy Landau on 2023-06-10
> **TheFu said:**
> I see the double-check on bigger/smaller being a good thing.
I agree. It would be a bit confusing otherwise!
> **TheFu said:**
> Did you vastly resize down the "root".  /, LV to have more flexibility in the future?
No, as I have just the two partitions: Root and swap. If I had separate partitions for everything, there'd be quite a bit of wasted space, and I my SSD isn't that big. (I haven't resized the partitions yet; I might do so today after doing a second emergency backup.)
> **TheFu said:**
> … using snapshots …
They would be nice, if I had a bigger disk! Instead, I do daily backups both online (offsite) and offline (onsite).
> **Quarkrad said:**
> A bit off topic but could you expand a bit on this **VMs that use LVs directly as raw disks**?
I'm not certain what TheFu means, but I think that it's this…

Usually, when you create a VM, you also create a virtual disk, which is really a file on your system, for that VM. But, it's possible for a VM to access a partition directly. For example, if you have Windows on your computer and you've been dual-booting, it's possible instead to boot only Linux, and use a VM to access Windows that way, so you never have to dual-boot. Caveats apply, and I've never tried it.

The partition can be an actual one on the disk, or it can be a virtual partition that LVM has created. LVM has certain advantages over physical partitions, including being able to span physical disks.

TheFu, if you meant something else, please let us know!

---

### Post by MAFoElffen on 2023-06-10
To expand on that, with KVM... Virsh and Virtual Manager has a facility for using LVM VG's as your Virutal Storag ePool back-end... What you do it set up a VG to use as your VM image storage pool back-end, then use LV's as your virtual disks instead of disk image files. 

I used to do it this way years ago on KVM on LTS 10.04. I think Dennis N or someone else told me that he does it this way now(?) I don't remember who now. 

Re:
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/create-lvm-storage-pool-virsh](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/create-lvm-storage-pool-virsh)
[https://bashtheshell.com/guide/configuring-lvm-storage-for-qemukvm-vms-using-virt-manager-on-centos-7/#](https://bashtheshell.com/guide/configuring-lvm-storage-for-qemukvm-vms-using-virt-manager-on-centos-7/#)

You can also setup virtual storage pool back-ends with ZFS and BTRFS. Though, I think that LVM2 is really better suited for this.

The advantages are that you can use the facilities of the file managers to do things live and online, along with doing snap shots, etc. Of the 3, I feel that LVM2 is easier to shrink and grow, while online, without the filesystem going into a degraded state. 

When you really think about it... Logically, it seems weird when you install a VM with LVM inside it's image, and know it resides inside of LVM on the host (nested). It seems to do this without any hit on performance.

---

### Post by Paddy Landau on 2023-06-10
> **MAFoElffen said:**
> It seems to do this without any hit on performance.
That's impressive, and probably also applies if you use LUKS encryption on the physical partitions. Modern hardware really helps with all of this.

---

### Post by TheFu on 2023-06-10
> **Quarkrad said:**
> A bit off topic but could you expand a bit on this **VMs that use LVs directly as raw disks**?  To date I have created a lv, formatted it as ext4 and then created the vm.

libvirt supports many, many, backend storage methods.  LVM is one of them.  If you use virt-manager and tell it about an LVM storage "pool", then it is trivial (and FAST!) to provide a new LV to any VM as raw storage.

For example, on a VM host here, I have some LVs:
```
$ sudo lvs
  LV                VG             Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  Mint21.1          vg00           -wi-ao----   40.00g                                                    
  lv-blog44         vg00           -wi-ao----   16.20g                                                    
  lv-regulus        vg00           -wi-a-----   30.00g                                                    
  lv-regulus-2      vg00           -wi-a-----   10.00g                                                    
  lv-vpn09-2004     vg00           -wi-ao----    7.50g                                                    
  lv-xen41-1804     vg00           -wi-ao----   12.50g                                                    
  lv-zcs45-1804     vg00           -wi-ao----   25.00g                                                    
  lxd               vg00           -wi-ao----   50.00g                                                    
  ubuntu22.04-srv-2 vg00           -wi-ao----   15.00g                                                    
  ubuntu2204-srv    vg00           -wi-ao----   15.00g                
```                                    

Inside each host system, they appear like any other HDD and can be resized from the outside (on the host) with a trivial lvextend command.  Inside, each VM, the disk becomes larger, like magic, and we just need to make use of that added storage.

I assume everyone here knows that LVM makes LVs really, really, fast and putting an ext4 file system onto any LV is probably 10x-100x faster than with normal partitions or qcow2 files.  

Plus, we can take snapshots of the storage for whatever purpose we might like.  Typically, I do snapshots to freeze blocks for backups, do the backup, then delete the snapshot.  It is a backup step to ensure running systems with open files don't create corrupt backups.

If you notice the lxd LV, that's used as ZFS storage by LXD for LXC containers.  Since I don't really use ZFS, but LXD really likes ZFS, this is a compromise.  That system has 5 lxc containers running using that LV storage, BTW,  One of those is nextcloud.  Another is an x86-64 pi-hole instance for DNS on my LAN and massive internet DNS filtering.  LXD does support snapshots on ZFS storage. It also supports creating a tar.gz "backup" of each container.  tar.gz backups are fine for non-professionals, but they suck for daily, versioned, backups which are much, much, much, more efficient for time-to-backup and storage used.

Best of all with LVs provided as raw storage, they aren't mounted on the hosts, so effectively the host and users don't really see the storage inside a VM unless they use LVM tools. Nobody will **sudo rm -rf ** and accidentally delete all the VMs on a system. Did I mention that LVs are much faster than file-based VM storage?

Anyway, hope this is clear.

---

### Post by Dennis N on 2023-06-10
> The advantages are that you can use the facilities of the file managers to do things live and online, along with doing snap shots, etc. Of the 3, I feel that LVM2 is easier to shrink and grow, while online, without the filesystem going into a degraded state.

Exactly. My main reason for the LV storage option was ease of expanding the disk size. It was more difficult with qcow2 storage.

In fact, there is a thread from May 2022 I started about VM storage expansion and how to do it. There were four cases I looked at, and the summary post is here:
[https://ubuntuforums.org/showthread.php?t=2475362&p=14097461#post14097461](https://ubuntuforums.org/showthread.php?t=2475362&p=14097461#post14097461)

Case 2 was marked "maybe" because of the impasse encountered on post #6 of that thread. A solution for this case was discovered shortly thereafter and is described in post #14.

---

### Post by Paddy Landau on 2023-06-10
> **TheFu said:**
> Inside, each VM, the disk becomes larger, like magic, and we just need to make use of that added storage.
How does that happen? Does it use compression?
> **TheFu said:**
> I assume everyone here knows that LVM makes LVs really, really, fast and putting an ext4 file system onto any LV is probably 10x-100x faster than with normal partitions or qcow2 files.
I did not know that!

So, what you're saying is that when I get a new computer with much more disk space than I have now, I should use LVM to create a logical partition for each virtual machine, and use that as its disk, instead of the usual file-as-a-virtual-disk? Have I understood you correctly? (The big advantage of using a file is that it can be dynamically sized, so that it uses only as much space as the VM actually uses.)

---

### Post by TheFu on 2023-06-10
> **Paddy Landau said:**
> How does that happen? Does it use compression?
lvextend on the host to expand the existing LV used by the VM. Guess I wasn't clear on that.

> **Paddy Landau said:**
> 
I did not know that!

So, what you're saying is that when I get a new computer with much more disk space than I have now, I should use LVM to create a logical partition for each virtual machine, and use that as its disk, instead of the usual file-as-a-virtual-disk? Have I understood you correctly? (The big advantage of using a file is that it can be dynamically sized, so that it uses only as much space as the VM actually uses.)

When I say 10-100x faster, I mean for just creation and formatting, not day to day use, though I think LVM does a bit of caching and is a tiny bit faster than non-LVM storage.

For fun, time these 2 tasks on YOUR COMPUTER with the same HDD.
a) create a partition and format it with ext4.
b) create an LV and format it with ext4.
I've formatted a 4TB ext4 partition in about 20 seconds.  I think it took 5 minutes without LVM.

Allocating storage for a new VM with LVM is basically instantaneous and handled inside virt-manager.

I use LVM on VMs with 15G or VMs with 40G or systems with 64G eMMC storage.  It is just so convenient that NOT using LVM baffles my mind that anyone with more than 4 yrs Linux experience isn't using some volume manager - LVM, ZFS, BTRFS.  LVM has the most decades of production use on Linux.
For advanced LVM users, check out "sparse LVs".  These share storage and can be resized as needed, automatically.  This is how hosting providers can oversell storage they don't have for thousands of clients on the same host system.  Hook up a 10TB HDD and tell every client they get 10G of storage. Most will use 2-8GB, to stay under their max use allowed.  That leaves 2G+ on each client that could be used by others.  *Oversubscribing* as this is known happens all the time in many different industries.  The phone company has been doing it over 100 yrs.  They don't have enough lines for everyone to make a call at the same time. Actually, people would be surprised at how high telephone oversubscription actually is.  Hotels, airlines, hospitals, telecommunications, internet are all built for typical loads, not peak loads.  This is why some phone calls don't go through on Mother's day or why your hotel "reservation" was lost when you arrive after 7pm or why your video streaming stutters in the evenings.  We can do the same with LVM. ;)   Or ... don't if it is your stuff.


I think ZFS has been ready for data about the last 8 yrs, but not to boot Ubuntu OSes.  Maybe in 22.04 ZFS is ready for production use as the OS storage too.  I know that my testing of ZFS on 20.04 booting ended badly and I wiped the storage, then put LVM+ext4 onto it.  ZFS gets used **inside** LXD/LXC containers.  Here's one:
```
$ dft
Filesystem             Type           Size  Used Avail Use% Mounted on
lxd/containers/pihole2 zfs             34G  2.4G   32G   7% /
snapfuse               fuse.snapfuse   64M   64M     0 100% /snap/core20/1879
snapfuse               fuse.snapfuse  112M  112M     0 100% /snap/lxd/24322
snapfuse               fuse.snapfuse   54M   54M     0 100% /snap/snapd/19361
snapfuse               fuse.snapfuse   54M   54M     0 100% /snap/snapd/19122
snapfuse               fuse.snapfuse   64M   64M     0 100% /snap/core20/1891
```
The 34G is shared by all LXC containers on the host, so the pihole is using 2.4G and all of the other storage is available for existing or now LXC containers.

BTRFS seems fine for 1-disk systems, though I've never used it myself.  We all had high hopes for that filesystem+volume manager.  Redhat removed BTRFS from their support for a few years. Some of their clients had data loss.  BTRFS came back to RHEL a few years ago, but I think they have some caveats now.  It isn't for everyone.

---

### Post by Paddy Landau on 2023-06-10
> **TheFu said:**
> It is just so convenient that NOT using LVM baffles my mind that anyone with more than 4 yrs Linux experience isn't using some volume manager
I think that it's not well known, really. I guess that LVM's marketing has been poor (unsurprising seeing as it's FOSS). There are aspects that you've been teaching me in this thread that I didn't know about LVM.
> **TheFu said:**
> For advanced LVM users, check out "sparse LVs".  These share storage and can be resized as needed, automatically. …
Now, that is useful! I think that I should take an hour or two to learn about that when I have some time.
> **TheFu said:**
> I think ZFS has been ready for data about the last 8 yrs, but not to boot Ubuntu OSes.
Canonical wanted to include ZFS, already back in 19.10, but [something happened]("https://www.omgubuntu.co.uk/2023/01/ubuntu-zfs-support-status") and Canonical decided that it wasn't worth doing.

Thanks for the information. It's interesting. I think that I could live an entire second lifetime doing nothing but Linux, and still not know all!

---

### Post by Dennis N on 2023-06-10
F.W.I.W. since we're talking LVM here:

With the new "Ubuntu Desktop Installer" seen in Ubuntu 23.04, the only way to do a new install of Ubuntu using LVM is to use "Erase Disk and Install Ubnutu". Installing to an existing LV using the manual partitioning option is not possible.

This has been mentioned in other threads here as well.

This situation may be only with the current state of development of this new installer. We'll see.

Screenshot: the only LVM install option.

---

### Post by Paddy Landau on 2023-06-10
> **Dennis N said:**
> With the new "Ubuntu Desktop Installer" seen in Ubuntu 23.04, the only way to do a new install of Ubuntu using LVM is to use "Erase Disk and Install Ubnutu". Installing to an existing LV using the manual partitioning option is not possible.
This has been the case for a while, but I wonder if there's a way to work around this? If I have time tomorrow, I'll test this in a VM.

---

### Post by Dennis N on 2023-06-10
> **Paddy Landau said:**
> This has been the case for a while, but I wonder if there's a way to work around this? If I have time tomorrow, I'll test this in a VM.

I installed 22.10 as LVM with the old Ubiquity installer, and the manual install screen detected existing logical volumes. So it was possible at that time.

---

### Post by Paddy Landau on 2023-06-10
Update: I made a full backup, ran fsck against the ext4 LVM partition, and then I resized the LVM partitions as instructed. It worked like a charm. I was impressed by how fast my ext4 partition was resized; it took less than a minute!

Thanks again to everyone.

---

### Post by Dennis N on 2023-06-10
> **Paddy Landau said:**
> Update: I made a full backup, ran fsck against the ext4 LVM partition, and then I resized the LVM partitions as instructed. It worked like a charm. I was impressed by how fast my ext4 partition was resized; it took less than a minute!

Thanks again to everyone.

Fine, but what if your disk already has one or more installs on it that you want to keep? You have to erase them to proceed with your LVM install.

---

### Post by Paddy Landau on 2023-06-10
> **Dennis N said:**
> Fine, but what if your disk already has one or more installs on it that you want to keep? You have to erase them to proceed with your LVM install.
I already have LVM. I used the full-disk installation with encryption when I installed Ubuntu. It creates a LUKS-encrypted partition, and then uses LVM to create the partitions. Only the EFI System Partition and the Boot partitions are outside that, because they're needed to boot the system in the first place.

---

### Post by Dennis N on 2023-06-10
> **Paddy Landau said:**
> I already have LVM. I used the full-disk installation with encryption when I installed Ubuntu. It creates a LUKS-encrypted partition, and then uses LVM to create the partitions. Only the EFI System Partition and the Boot partitions are outside that, because they're needed to boot the system in the first place.

OK. we are talking about different situations. I was responding to your comment in post 23 " If I have time tomorrow, I'll test this in a VM" in mind. Post 25 was not about that planned test.

---

### Post by Paddy Landau on 2023-06-10
> **Dennis N said:**
> OK. we are talking about different situations. I was responding to your comment in post 23 " If I have time tomorrow, I'll test this in a VM" in mind. Post 25 was not about that planned test.
Ah, yes, sorry. My post was about my initial request in this thread. Discussions can veer quite off course can't they! I learn a lot that way, one of the reasons why I love this forum.

---

### Post by MAFoElffen on 2023-06-10
A few things... LVM and ZFS make it really easy to move data from place to place... drive to drive... even machine to machine.

LVM2 is really seasoned and has been production-ready for ions. I've been using LVM2 since around 10.04. I think it was TheFu who helped me way back when, when I as changing out an LVM root drive on one of my servers to something larger.

I've been using ZFS since 2015... But first on OpenSolaris and then on Solaris. It has not been on Linux for that long in it's present form. I used it when it was early zfs-fuse on Linux (ubuntu 12.04). I wasn't happy at the challenges that brought with it. I am very happy with it's current OpenZFS form. About 2/3rds of my current machines are ZFS-on-Root. The main server has an NVMe RAIDz pool and a SSD RAIDz pool for my KVM images. The bandwidth and throughput is astronomical and I am very happy with it. My other KVM server is still LVM2 based and spun disks... I didn't realize just how much the performance different was until I got them side-by-side, and benchmarked them. There is issues with licensing concerns, but that is a story in itself.

BTRFS... is still growing and working things out. It isn't production ready yet. I have hopes for it.

1fallen and I are trying to keep ZFS alive in Ubuntu, and accessible for Users... I have a Bug Report open on it for the new installer. They crippled it, and how they say they still have it as an option is an outright lie, which I called then out on that. They have it there, orphaned as a 'file type'.

The new (since 23.04) 'ubuntu-desktop-installer' snap based installer has big problems and short comings. The biggest issue is that the partitioner used with that is "[COLOR=#ff0000]not filesystem aware[/COLOR]"... Which means for LVM2, BTRFS, LUKS, and ZFS, you can no longer setup a filesystem in a terminal, then start the installer, get to the partitioner, have it recognize the filesystem there, and install to it. That is my (and many others) go-to for setting up LVM2 systems. (And other file systems and file management containers)

<The Server Live Installer still works. It has not changed. I am referring to the Desktop installer.>

I really feel that we need some help in pushing them to correct this. This affects more than just LVM2. I noticed this right off, early in the Lunar Development cycle. They need to get that worked out ad working before 24.04.

Please join this bug and weight in how important this is to you as Users: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

I think once they fix the partitioner there to be filesystem aware, then it will be easier for us to use other file managers again.

Sorry for that sideline, but I feel this is really very important to us all.

---

### Post by #&amp;thj^% on 2023-06-10
> **MAFoElffen said:**
> A few things... LVM and ZFS make it really easy to move data from place to place... drive to drive... even machine to machine.

LVM2 is really seasoned and has been production-ready for ions. I've been using LVM2 since around 10.04. I think it was TheFu who helped me way back when, when I as changing out an LVM root drive on one of my servers to something larger.

I've been using ZFS since 2015... But first on OpenSolaris and then on Solaris. It has not been on Linux for that long in it's present form. I used it when it was early zfs-fuse on Linux (ubuntu 12.04). I wasn't happy at the challenges that brought with it. I am very happy with it's current OpenZFS form. About 2/3rds of my current machines are ZFS-on-Root. The main server has an NVMe RAIDz pool and a SSD RAIDz pool for my KVM images. The bandwidth and throughput is astronomical and I am very happy with it. My other KVM server is still LVM2 based and spun disks... I didn't realize just how much the performance different was until I got them side-by-side, and benchmarked them. There is issues with licensing concerns, but that is a story in itself.

BTRFS... is still growing and working things out. It isn't production ready yet. I have hopes for it.

1fallen and I are trying to keep ZFS alive in Ubuntu, and accessible for Users... I have a Bug Report open on it for the new installer. They crippled it, and how they say they still have it as an option is an outright lie, which I called then out on that. They have it there, orphaned as a 'file type'.
I did as well in another venue, got the same reply as you did, until I challenged a Dev to actually look, well now it's clear.
> **MAFoElffen said:**
> 
I really feel that we need some help in pushing them to correct this. This affects more than just LVM2. I noticed this right off, early in the Lunar Development cycle. They need to get that worked out ad working before 24.04.

Please join this bug and weight in how important this is to you as Users: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

I think once they fix the partitioner there to be filesystem aware, then it will be easier for us to use other file managers again.

**Sorry for that sideline, but I feel this is really very important to us all.**
**I as well am sorry for the Off Topic but it is important that we act now on this please!!!** (It takes less than 5 mins Tops to add yourself to that Bug)
And it is the right thing to do......Again PLEASE!

---

### Post by TheFu on 2023-06-10
> **Paddy Landau said:**
> Update: I made a full backup, ran fsck against the ext4 LVM partition, and then I resized the LVM partitions as instructed. It worked like a charm. I was impressed by how fast my ext4 partition was resized; it took less than a minute!

Thanks again to everyone.

I'm confused.  Take a look at the attached diagram.

Only an LV (logical volume) should be holding a file system and only the file system should have an fsck run against it, not on a partition where an LVM PV (physical volume) is placed.  

fsck can't be run against a VG, Volume Group, either.  Running fsck against the wrong types of objects can be dangerous.

**>>>>>    fsck should only be run against an object that holds a file system.   <<<<<**

Resizing LVs should take less than 5 seconds if the file system is ext4 and the resizefs (-r) option is included in the **lvextend** command.  If it takes longer, the drive is spinning down and very slow to start.

>  A few things... LVM and ZFS make it really easy to move data from place to place... drive to drive... even machine to machine.

At the VG and PV level, it is really easy.  At the LV level, not so much, unless you are willing to split off the LV into a new, separate VG first.  When I needed to migrate some LVs between systems and didn't want to create new, fresh, VGs with the same name or unplug the SSD to move it, I wrote a little ugly script to generate a few commands (to prevent my human failures) to copy/paste into the source and target systems.  No error checking and many manual things still needed, so it isn't safe for others to use.

The manual parts to the migration include dumping the source XML VM config file and manually editing it for the different LVname and bridge on the new system.

I used netcat to move the LV because I don't allow remote root ssh. Allowing that would be a hassle AND slower.  netcat running as root on both sides (systems) can transfer the LV block at wire speeds between 2 SSDs - effectively making is 20 seconds to transfer an 18GB LV.  Plus, I wanted to drop the migrated LV directly into the newly created LV on the target system, not into a temporary location first.

I should have created a new VG with a specific name just to be used for virtual machine that need to be moved back and forth between systems to aid maintenance on both systems.  Hummmmm.  I need to sleep on that idea a bit.  **vgexport** and **vgimport** are mostly logical helpers for physically moving storage. But pvmove is A-W-E-S-O-M-E!  Migrating an entire PV to a new disk all while the system keeps working.

If I need to move LVs around much more, need to make that hack script better and more automated, I suppose.

As long as LVM is possible in an installer, I don't really need/want for the installer to push their crappy layout onto me.  For the last few years, I've been pre-creating the disk layout I want. Think MAFoElffen turned me on to that.  Before I'd just accept what the default did with "Use LVM" checked, then go back and fix it.  Now I use a script in a different TTY during the install - before "Do Something Else" in the storage options to setup partitions and LVM how I prefer. Saves moving /home/,  /var/ and /tmp/ post install to new LVs.  Also, for a long time, the LVM creation would use MBR partition tables, not GPT, even if I'd specifically created a GPT table on the disk.  That was maddening.  I nearly cried with 20.04 didn't wipe the GPT and put MBR instead.  It doesn't take much to make me happy.

**Even more OT:**
So, when will Ubuntu default to LDAP (local and remote) for user and group accounts?  It is embarrassing that MS-AD is an option, but not connecting to a normal Linux LDAP server.  At least, I'd be embarrassed if I put out a distro that wanted to be taken serious inside an enterprise, but didn't support Unix LDAP servers easily.

---

### Post by Dennis N on 2023-06-10
> Please join this bug and weight in how important this is to you as Users: [https://bugs.launchpad.net/ubuntu-de...r/+bug/2014977](https://bugs.launchpad.net/ubuntu-de...r/+bug/2014977)
Done!

---

### Post by Paddy Landau on 2023-06-11
> **MAFoElffen said:**
> The biggest issue is that the partitioner used with that is "[COLOR=#ff0000]not filesystem aware[/COLOR]"...
That sucks. I've voted on the bug report.

---

### Post by Paddy Landau on 2023-06-11
> **TheFu said:**
> I'm confused. … Only an LV (logical volume) should be holding a file system…
Sorry, that's my wording. I ran fsck against the (unmounted) ext4 LV.
> **TheFu said:**
> Resizing LVs should take less than 5 seconds if the file system is ext4 and the resizefs (-r) option is included in the **lvextend** command.
Maybe it did take less than 5 seconds! I wasn't paying attention to the time (I went and did something else, expecting it to take a while), and then noticed it had already finished in under a minute.

How is it so quick? I thought that when you shrink a volume, it had to move any data in the part to be freed?
> **TheFu said:**
> But pvmove is A-W-E-S-O-M-E!  Migrating an entire PV to a new disk all while the system keeps working.
That's amazing! I didn't know that such a thing was possible.

---

### Post by MAFoElffen on 2023-06-11
Practical example... Change out a bad disk, or move to a larger disk: 

Partition a new disk as 8e00 (Linux LVM). Prepare the new partition for LVM (pvcreate). Add that partition to a VG (vgextend). ID the device name of the VG (vgscan). Use that device name in the pvmove command to move the data from the old partition to the new partition (off the old disk). Use vgreduce to remove the old partition from the VG. Use pvremove to remove it as a PV device. (also wipes it.) And this can all be done online, with the filesystem live. The only time to need to reboot, is if you are replacing a root drive, to boot off the new drive and remove the old (physically).

If you have more than one disk... a VG spanning over many disks, that is how you change out a disk, or add larger disks into your storage... Rotating out the bad, older or smaller disks.

@TheFu -- LVM2 Command for you to explore and play with: [Ubuntu man page 'vgspilt]("https://manpages.ubuntu.com/manpages/bionic/man8/vgsplit.8.html")' I'm thinking this will give you some ideas...

---

### Post by TheFu on 2023-06-11
> **MAFoElffen said:**
>  

@TheFu -- LVM2 Command for you to explore and play with: [Ubuntu man page 'vgspilt]("https://manpages.ubuntu.com/manpages/bionic/man8/vgsplit.8.html")' I'm thinking this will give you some ideas...

Years ago, I went through all the vg*, pv* and lv* commands to see what they did.  I'd forgotten about vgsplit, but remember now. 
I always use the local manpages, not web-based manpages. Got burned a few times where the web and the local version of some program were different enough to matter.  Unfortunately, pretty much all of the systemd manpages have "aspirational" content - things not implemented, but planned, someday.  Either that, or it is stuff that doesn't actually work.

---

