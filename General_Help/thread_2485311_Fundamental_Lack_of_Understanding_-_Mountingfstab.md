---
title: "Fundamental Lack of Understanding - Mounting/fstab"
date: 2023-03-27
forum: General Help
---

### Post by Quarkrad on 2023-03-27
I had the dreaded *0 disk space in root* window pop up and my Desktop was virtually locked up.  I have recently migrated to lvm and also installed a number of snap applications because,  although I'm not too keen on snap myself, a number of my non-techie friends/neighbours could benefit from the snap philosophy and I wanted some real world testing rather than just using a vm.   Anyway, my first thought was snap was to blame and I started to remove snap but then stopped - I believe you need snap for LVM.  Having said that, I do not think my root partition was full because of snap.  This is how I initially set up my new 1TB HD:

```
dad@dadubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg01/root
  LV Name                root
  VG Name                vg01
  LV UUID                Q9V1MZ-K1yj-KyPB-Ax2Q-Cehr-yrxK-L9uVH3
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:48:57 +0000
  LV Status              available
  # open                 1
  LV Size                40.00 GiB
  Current LE             10240
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vg01/home
  LV Name                home
  VG Name                vg01
  LV UUID                k2I519-SiTv-PXYV-LBTB-Bquo-3jm8-LVgvgU
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:49:35 +0000
  LV Status              available
  # open                 1
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
```

My thinking that 40GB for / would be plenty big enough (and I could potentially increase it using lvm in the future if needed).  I have added a number of other logical volumes to my 1T HD so the full disk looks like:

```
dad@dadubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg01/root
  LV Name                root
  VG Name                vg01
  LV UUID                Q9V1MZ-K1yj-KyPB-Ax2Q-Cehr-yrxK-L9uVH3
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:48:57 +0000
  LV Status              available
  # open                 1
  LV Size                40.00 GiB
  Current LE             10240
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vg01/home
  LV Name                home
  VG Name                vg01
  LV UUID                k2I519-SiTv-PXYV-LBTB-Bquo-3jm8-LVgvgU
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2023-02-21 15:49:35 +0000
  LV Status              available
  # open                 1
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/vg01/workspace
  LV Name                workspace
  VG Name                vg01
  LV UUID                E2gsIe-lcni-ROxO-UIm8-KnLv-5dAl-p3NhT2
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-02-21 20:45:28 +0000
  LV Status              available
  # open                 0
  LV Size                250.00 GiB
  Current LE             64000
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2
   
  --- Logical volume ---
  LV Path                /dev/vg01/swap
  LV Name                swap
  VG Name                vg01
  LV UUID                LtHzWU-FlDd-EzCB-4VGg-vR5E-hD86-HFV7f8
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-02-27 12:58:47 +0000
  LV Status              available
  # open                 2
  LV Size                8.00 GiB
  Current LE             2048
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:3
   
  --- Logical volume ---
  LV Path                /dev/vg01/ubuntu2204vm
  LV Name                ubuntu2204vm
  VG Name                vg01
  LV UUID                776QpH-h2qC-DDEr-rfmc-mUJ2-ceaK-o9D5VV
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-02-27 13:55:03 +0000
  LV Status              available
  # open                 0
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:4
   
  --- Logical volume ---
  LV Path                /dev/vg01/win10vm
  LV Name                win10vm
  VG Name                vg01
  LV UUID                rlwIJ1-C6Ze-uvYf-1LLP-VAMV-Ij4B-irKgvy
  LV Write Access        read/write
  LV Creation host, time dadubuntu, 2023-03-26 08:22:24 +0100
  LV Status              available
  # open                 0
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:5

```

Having created these additional logical volumes I have to mount them so put then in */media/dad/* - which is normal for me but I think this is why my understanding is wrong.

When I had 0 disk space in / this was how my system looked:

```
dad@dadubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root      ext4   40G   38G   25M 100% /
/dev/nvme0n1p1             vfat  197M  6.1M  191M   4% /boot/efi
/dev/mapper/vg01-home      ext4   49G   14G   33G  30% /home
/dev/sdb1                  ext4  1.8T  485G  1.3T  28% /media/dad/backup
/dev/mapper/vg01-workspace ext4  246G  163G   71G  70% /media/dad/workspace
```

(Please ignore */dev/sdb1* - I have other hd in my Desktop that are NOT part of the lvm environment.  These are purely backup and data storage devices that rarely change.  The lvm environment is purely on the 1TB HD where / and /home are).  At this point I can clearly see that my 40GB root lv is 100% used.   Having now suspected that snap may not be the total culprit (looking at the size of /var, /etc, /usr, etc) I questioned my mounting these extra logical volumes in */media*, which is part of /.  So ... I have commented out these extra logical volumes from fstab and deleted their mount points in /media.  Now I have:

```
dad@dadubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem            Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root ext4   40G   14G   24G  37% /
/dev/nvme0n1p1        vfat  197M  6.1M  191M   4% /boot/efi
/dev/mapper/vg01-home ext4   49G   12G   35G  26% /home
/dev/sdb1             ext4  1.8T  487G  1.3T  28% /media/dad/backup1

```

(Again please ignore */dev/sdb1*)

My root usage has gone from 100% to 37%.  This makes sense to me in one way in that */media* is part of root and I was filling it up but is it not true that everything is under / (root).  Where should I mount my extra logical volumes such that I do not fill up my 40GB root volume?

---

### Post by TheFu on 2023-03-27
> **Quarkrad said:**
>  I believe you need snap for LVM.  

This is incorrect.  Perhaps you are confusing LVM and LXD?

I haven't used lv/vg/pv/display commands in years.
pvs, vgs, and lvs are much cleaner.

If you are planning to use snap packages, then create a new LV and mount it to /var/lib/snapd/ to hold all that junk. Or you could make an LV for /var/ ... just be certain it is at least the size needed for logs (2G) and whatever snaps you'll install and whatever lxd containers you'll create.  That could be 15G - 1TB, easily. Just depends on use.

Mount points are usually just empty directories.  Then we mount an existing file system to that empty directory.  If the mount fails and we don't validate it, then whatever space / has will be used.  For backup storage, it is very important to ensure the separate backup file system is actually mounted where and when needed.

---

### Post by Quarkrad on 2023-03-27
I don't think I'm confusing LXD and LVM, but perhaps I am.  At the moment I have two logical volumes that I have created to be used as VMs - */dev/vg01/ubuntu2204vm* and */dev/vg01/win10vm*.  These are sitting on my 1T HD - my lack of knowledge is how/where to mount them so they are visible in my file manager.  As above, when I mount them in fstab to */media/dad/* I blow / to bits and run out of space. When they were mounted at */media/dad* my / was 100% - when I unmounted them my / was 37%.  I believe I don't really understand what is going on.  Over the years if I wanted to 'see' something like a partition or HD in the file manager I would have an entry in fstab and if necessary create a folder in */media*.  This is the first time I've create a folder in /*media*, so that I can see the VM (e.g. */dev/vg01/ubuntu2204vm*) in my file manager, that it has filled up /.

---

### Post by TheFu on 2023-03-27
If you are providing the LV to the VM, there's no need for it to be mounted on the hostOS at all.  For example:
 ```
NAME                              SIZE TYPE FSTYPE      MOUNTPOINT
sdb                               477G disk             
&#9500;&#9472;sdb1                            731M part ext2        /boot
&#9500;&#9472;sdb2                              1K part           
&#9492;&#9472;sdb5                          476.2G part LVM2_member
  &#9500;&#9472;hadar--vg-root               32.3G lvm  ext4        /
  &#9500;&#9472;hadar--vg-swap_1              4.3G lvm  swap        [SWAP]
  &#9500;&#9472;hadar--vg-libvirt--lv         175G lvm  ext4        /var/lib/libvirt
  &#9500;&#9472;hadar--vg-lxd--lv              60G lvm  ext4        /var/lib/lxd
  [B]&#9500;&#9472;hadar--vg-lv--vpn09--2004     7.5G lvm
  &#9500;&#9472;hadar--vg-lv--xen41          12.5G lvm
  &#9500;&#9472;hadar--vg-lv--zcs45            25G lvm
  &#9500;&#9472;hadar--vg-lv--regulus          30G lvm
  &#9500;&#9472;hadar--vg-lv--regulus--2       10G lvm
  &#9500;&#9472;hadar--vg-lv--tp--lxd_tmeta   108M lvm
  &#9474; &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm
  &#9500;&#9472;hadar--vg-lv--tp--lxd_tdata  32.2G lvm
  &#9474; &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm
  &#9492;&#9472;hadar--vg-lv--blog44         16.2G lvm
[/B]
```
I've 'bolded' the LVs that are for VM (or lxd) use, but aren't mounted on the hypervisor file system.  Having 2 OSes accessing the same storage is asking for corruption.

---

### Post by Quarkrad on 2023-03-28
I don't understand 'having 2 OSes accessing the same storage is asking for corruption'.  If there was only one HD in a PC then is this saying one cannot have any VMs more than one VM because there is only one storage medium by definition?  Pre LVM I had multiple VMs all on the same physical partition.  

If the LV/VMs are not mounted (so not visible in the file manager) do you have to remember where there are and how they are accessed in order to use them? (I guess a script could be used to launch each VM)

But I still come back to my original question - how/where do I mount these LV/VMs so they do not fill up /?   (Is this something specific to LVM because I have never had this issue before?)

---

### Post by The Cog on 2023-03-28
Running both VMs *at the same time* will end in corruption. Each VM will have its own opinion of what's on the disk and where to write new stuff, without any knowledge that the other VM is writing stuff to the drive too. Both VMs will be doing disk caching so they won't see what each other are doing, they will just be updating and writing their changes on top of what they ***think*** is on the disk.
Same applies to mounting concurrently on guest VM and host.

---

### Post by The Cog on 2023-03-28
Duplicate post.

---

### Post by Quarkrad on 2023-03-28
Thank you - that explains it.  My scenario is a stand-alone Desktop used for general purpose computing.  I do not use VMs that much - and have never had the need, to run them concurrently.  I have a ubuntu VM so that if I'm not sure about installing something on my Desktop, if will install it on my VM to see if it does what I want.  E.g. I played with rdiff-backup for some time on my VM before I understood it well enough to use it on my main Desktop.  I have another VM for win10 I occasionally use for those friends I support who have a win10 machine.

I'm still confused why mounting my VMs causes / to fill up when it has never been an issue before.

---

### Post by Quarkrad on 2023-03-28
For some reason everything is working OK.  I re-enabled my VMs in fstab and df -h is showing / as 37%  (14GB used).  In some ways I wish I had a solution but it looks like there never was a (fundamental) problem just perhaps a glitch - at least this proves my (basic) understanding of mounting and fstab was correct.  Thank you for helping me understand more with your comments above.

---

### Post by TheFu on 2023-03-28
> **Quarkrad said:**
> Thank you - that explains it.  My scenario is a stand-alone Desktop used for general purpose computing.  I do not use VMs that much - and have never had the need, to run them concurrently.  I have a ubuntu VM so that if I'm not sure about installing something on my Desktop, if will install it on my VM to see if it does what I want.  E.g. I played with rdiff-backup for some time on my VM before I understood it well enough to use it on my main Desktop.  I have another VM for win10 I occasionally use for those friends I support who have a win10 machine.

I'm still confused why mounting my VMs causes / to fill up when it has never been an issue before.

The LV provided to the VM is a "block device" if you are using LVM in the best way.  It, the LV, would only be mounted inside the specific VM to which is it meant to be used.  The hostOS would only see it as part of an LV, inside a VG, inside a PV. The hostOS wouldn't see it as a file system, so it shouldn't be mounted in the hostOS at all.

Now, if you are creating an LV, then a file system on the hostOS and creating a qcow2 or vdi or img file for the virtual machine **inside** that file system, then LVM isn't really as useful, since the guest VM is using the qcow2 file as a block device, not the LV directly.  That is what my lsblkt output above is showing. From the hostOS, is sees LVs, but those LVs aren't mounted on the host.  Inside the VM, they are seen as block devices, have a partition table, partitions, and file systems.
For example, just to be clear, from the hostOS, here's the LVs provided to my 'regulus' VM:
```
NAME                              SIZE TYPE FSTYPE      MOUNTPOINT
sdb                               477G disk             
&#9492;&#9472;sdb5                          476.2G part LVM2_member
  &#9500;&#9472;hadar--vg-lv--regulus          30G lvm
  &#9500;&#9472;hadar--vg-lv--regulus--2       10G lvm
```
Inside regulus, it appears like this:

```
Disk /dev/vda: 30 GiB, 32212254720 bytes, 62914560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa55500b1

Device     Boot   Start      End  Sectors  Size Id Type
/dev/vda1  *       2048  1050623  1048576  512M  b W95 FAT32
/dev/vda2       1052670 62912511 61859842 29.5G  5 Extended
/dev/vda5       1052672 62912511 61859840 29.5G 8e Linux LVM

Disk /dev/vdb: 10 GiB, 10737418240 bytes, 20971520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FADD8143-17B4-E446-B328-34BCE660B93C

Device     Start      End  Sectors Size Type
/dev/vdb1   2048 20971486 20969439  10G Linux LVM

$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   19G   14G  4.0G  78% /
/dev/mapper/vgubuntu--mate-home ext4   16G   12G  3.3G  79% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
```

I'm using LVM inside the VM ... nested LVM, if you like. I used some LVM 'magic' to have 2 PVs, 1 VG, and resized the LVs to be a little larger.  It is sorta ugly. Still inside the guest VM:
```
$ lsblkt
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sr0                       1024M rom              
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     19G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     16G lvm  ext4        /home
vdb                         10G disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     19G lvm  ext4        /
  &#9492;&#9472;vgubuntu--mate-home     16G lvm  ext4        /home
$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vgubuntu-mate -wi-ao---- 16.00g                                                    
  root   vgubuntu-mate -wi-ao---- 19.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g  

$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree  
  /dev/vda5  vgubuntu-mate lvm2 a--  <29.50g      0 
  /dev/vdb1  vgubuntu-mate lvm2 a--  <10.00g 400.00m
```
vda and vdb are really from the same SSD on the host (they are just separate LVs after all), so spanning storage devices inside the guest isn't a terrible thing.  I wanted to see if I could add another disk while the systems kept running using LVM.  The answer is yes.  I could have also resized the LV lv--regulus from the hostOS, then tricked the guestVM to see the newly resized disk, but that would have required downtime, which I wanted to avoid for the exercise.

---

### Post by Quarkrad on 2023-03-28
Thank you - very interesting. You have got me into LVM and I am just getting my feet wet I will come back to the above in more detail further down my particular road!

---

