---
title: "add more swap to luks?"
date: 2024-04-15
forum: General Help
---

### Post by gingin2020 on 2024-04-15
how to make a swap bigger on luks?
by default it is only 2 GB 
I want 16GB swap




cat  /etc/crypttab
nvme0n1p3_crypt UUID=5453a2d7-a805-4c46-8830-1b40b4e0820b none luks,discard
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vgkubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/nvme0n1p2 during installation
UUID=6e64ffd7-9479-49aa-924e-189f61ea1158 /boot           ext4    defaults        0       2
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=E1D2-69BA  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vgkubuntu-swap_1 none            swap    sw              0       0


lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINTS
loop0 7:0 0 4K 1 loop /snap/bare/5
loop1 7:1 0 373.8M 1 loop /snap/anbox/186
loop2 7:2 0 105.4M 1 loop /snap/core/16574
loop3 7:3 0 104M 1 loop /snap/core/16928
loop4 7:4 0 63.9M 1 loop /snap/core20/2182
loop5 7:5 0 63.9M 1 loop /snap/core20/2264
loop6 7:6 0 74.1M 1 loop /snap/core22/1033
loop7 7:7 0 74.2M 1 loop /snap/core22/1122
loop8 7:8 0 267.5M 1 loop /snap/firefox/3941
loop9 7:9 0 268.3M 1 loop /snap/firefox/4090
loop10 7:10 0 349.7M 1 loop /snap/gnome-3-38-2004/140
loop11 7:11 0 349.7M 1 loop /snap/gnome-3-38-2004/143
loop12 7:12 0 497M 1 loop /snap/gnome-42-2204/141
loop13 7:13 0 504.2M 1 loop /snap/gnome-42-2204/172
loop14 7:14 0 91.7M 1 loop /snap/gtk-common-themes/1535
loop15 7:15 0 103.2M 1 loop /snap/pac-vs/1
loop16 7:16 0 147M 1 loop /snap/shotcut/1389
loop17 7:17 0 40.4M 1 loop /snap/snapd/20671
loop18 7:18 0 39.1M 1 loop /snap/snapd/21184
loop19 7:19 0 417.9M 1 loop /snap/telegram-desktop/5783
loop20 7:20 0 417.9M 1 loop /snap/telegram-desktop/5791
loop21 7:21 0 310.8M 1 loop
nvme0n1 259:0 0 953.9G 0 disk
&#9500;&#9472;nvme0n1p1 259:1 0 512M 0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:2 0 1.7G 0 part /boot
&#9492;&#9472;nvme0n1p3 259:3 0 951.7G 0 part
&#9492;&#9472;nvme0n1p3_crypt 252:0 0 951.7G 0 crypt
&#9500;&#9472;vgkubuntu-root 252:1 0 929.4G 0 lvm /var/snap/firefox/common/host-hunspell
&#9474; /
&#9492;&#9472;vgkubuntu-swap_1 252:2 0 1.9G 0 lvm [SWAP]




Filesystem Size Used Avail Use% Mounted on
tmpfs 1.6G 2.6M 1.6G 1% /run
/dev/mapper/vgkubuntu-root 914G 325G 543G 38% /
tmpfs 7.7G 298M 7.4G 4% /dev/shm
tmpfs 5.0M 4.0K 5.0M 1% /run/lock
efivarfs 246K 108K 134K 45% /sys/firmware/efi/efivars
/dev/nvme0n1p2 1.7G 301M 1.3G 20% /boot
/dev/nvme0n1p1 511M 6.1M 505M 2% /boot/efi
tmpfs 1.6G 108K 1.6G 1% /run/user/1000

---

### Post by TheFu on 2024-04-16
Without code-tags, it is too hard to read and you want as many people as possible to actually bother looking at your post, rihgt?  Make it easy to help you. Please.  Edit your post above to wrap all the terminal output in code tags.   [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains.

Please show the output from wrapped in forum code tags.
```
sudo pvs
sudo vgs
sudo lvs
```

LUKS encryption uses LVM, so those are the tools you'll need to see if there is spare room to do what you seek.

BTW, having a swap larger than 4GB is almost always a waste.

And you really shouldn't have allowed the root LV to be larger than 35GB.  Immediately post-install, you should have reduced the size down from whatever the installer did to 35GB, setup another LV for "home" and removed the default swap LV, then created a new 4GB swap.

Having the root LV at 914GB is an abomination and defeats the reason for using LVM.  LVM is best used where only the storage needed is allocated to LVs, most should be unused so that LVM snapshots can be used and for future flexible increases to the LVs that need a little more storage.  For example, here's my LVM setup:
```
NAME                                  TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL          MOUNTPOINT
nvme0n1                               disk                    931.5G                               
&#9500;&#9472;nvme0n1p1                           part  ext2                  1M                               
&#9500;&#9472;nvme0n1p2                           part  vfat                 50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3                           part  ext4                700M  339.8M    42%                /boot
&#9492;&#9472;nvme0n1p4                           part  LVM2_member       930.8G                               
  &#9500;&#9472;vg01-swap01                       lvm   swap                4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01                       lvm   ext4                 35G   24.8G    22%                /
  &#9500;&#9472;vg01-var01                        lvm   ext4                 20G     14G    23%                /var
  &#9500;&#9472;vg01-tmp01                        lvm   ext4                  4G    3.6G     1% tmp01          /tmp
  &#9500;&#9472;vg01-home01                       lvm   ext4                 20G     10G    44% home01         /home
  &#9500;&#9472;vg01-libvirt--01                  lvm   ext4                137G    2.8G    98% libvirt--01    /var/lib/libvirt
  &#9500;&#9472;vg01-lxd--containers--01          lvm                        30G                               
  &#9492;&#9472;vg01-ubuntu2310                   lvm                        15G                               
```
First, see how readable that is with code tags?
I've left off other storage that installed in the system that uses RAID and LVM, since it is only for data, not the OS.  
```
$ sudo vgs
  VG           #PV #LV #SN Attr   VSize    VFree   
  vg01           1   8   0 wz--n- <930.78g <665.68g

$ sudo lvs
LV                VG           Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
home01            vg01         -wi-ao----  20.00g                                                    
libvirt-01        vg01         -wi-ao---- 137.00g                                                    
lxd-containers-01 vg01         -wi-a-----  30.00g                                                    
root01            vg01         -wi-ao----  35.00g                                                    
swap01            vg01         -wi-ao----   4.10g                                                    
tmp01             vg01         -wi-ao----   4.00g                                                    
ubuntu2310        vg01         -wi-a-----  15.00g                                                    
var01             vg01         -wi-ao----  20.00g                                                    
```
As you can see, most of my 1TB NVMe storage isn't being used.  During backups, there are multiple snapshots active to ensure the backups don't have any corrupted files. LVM-snapshots completely quiesce the data while backup happens.  You can read more about this technique here: [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

Something looks wrong about your **lsblk** output. Perhaps it was wrapped in a funny way?  Also, there are lots of fake storage devices listed that are completely unimportant. Best to remove those, since they have no impact.  Any devices with "loop" in the name are fake.
**lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint** is the command I use.  The **-e 7** option removes the loop crap.

If you don't have any free space in the VG, then it will be impossible to increase (more likely delete and re-create) the swap LV.  So you'll likely want to move lots of storage around and definitely want to resize the "root" LV down to a reasonable size as your first step.

---

### Post by gingin2020 on 2024-04-16
[FONT=monospace]```
[/FONT][FONT=monospace][COLOR=#000000]sudo pvs[/COLOR]
sudo vgs
sudo lvs
  PV                          VG        Fmt  Attr PSize    PFree   
  /dev/mapper/nvme0n1p3_crypt vgkubuntu lvm2 a--  <951.68g <20.36g
  VG        #PV #LV #SN Attr   VSize    VFree   
  vgkubuntu   1   2   0 wz--n- <951.68g <20.36g
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgkubuntu -wi-ao---- 929.41g                                                     
  swap_1 vgkubuntu -wi-ao----  <1.91g 
[/FONT][FONT=monospace]
```
[/FONT]

---

### Post by MAFoElffen on 2024-04-16
Looks to me like he may like he has 20 GB of free space in VG  'vgubuntu' to play with to just expand/grow LV 'swap_1'

---

### Post by TheFu on 2024-04-16
> **MAFoElffen said:**
> Looks to me like he may like he has 20 GB of free space in VG  'vgubuntu' to play with to just expand/grow LV 'swap_1'

Yep, but that wouldn't be smart to use, since it would effectively remove any space for snapshots.
Better to reduce the "root" LV size ASAP.

 MAFoElffen, any comments about making a 16GB swap?  I stand behind my 4.1GB limit for all swap. It doesn't help to have any more. Just takes away space that won't be used much anyway.

A few years ago, we had a long thread here about the purpose and uses of swap.  All the discussion didn't change my 4.1GB size limitation at all.  Some swap is good. 4GB seems to be the sweet spot for desktop systems running bloated browsers. For servers, it is best to have "some" swap to turn on some performance options in the kernel, but since RAM is cheap, much smarter to setup any servers so they don't need any swap - definitely less than 500MB should be used by a properly tuned server.  

Of course, if you are running a paid service and want to make people "upgrade" to more expensive plans, then having little real RAM and 200GB of swap so their programs run very slow might be a business model.  I've seen at least 1 VPS do that.

---

### Post by aug7744 on 2024-04-16
@gingin2020 If you have more than 4 GB RAM you maybe use zram configured for 16 GB. The buffer used in ram will be more or less 5 GB.

---

### Post by TheFu on 2024-04-16
> **gingin2020 said:**
> [FONT=monospace]```
[/FONT][FONT=monospace][COLOR=#000000]sudo pvs[/COLOR]
sudo vgs
sudo lvs
  PV                          VG        Fmt  Attr PSize    PFree   
  /dev/mapper/nvme0n1p3_crypt vgkubuntu lvm2 a--  <951.68g <20.36g
  VG        #PV #LV #SN Attr   VSize    VFree   
  vgkubuntu   1   2   0 wz--n- <951.68g <20.36g
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgkubuntu -wi-ao---- 929.41g                                                     
  swap_1 vgkubuntu -wi-ao----  <1.91g 
[/FONT][FONT=monospace]
```
[/FONT]

Ok. We seem to be providing "why" and not exactly what to type, if you still want to go through with this.

First. Swap can't directly be made larger in a "good way".  
The way to do it is to disable the swap, then delete the old swap LV, then create a new swap LV, format it as "swap" and re-enable the swap.  For other file systems like ext4, we can just extend the LV AND resize the file system in 1 command, but swap is different.  Ok, so here are the commands, 
```
sudo swapoff /dev/vgkubuntu/swap_1
sudo lvremove /dev/vgkubuntu/swap_1
sudo lvcreate -L 4.1G vgkubuntu -n swap_1   # change the size to be the size you want
sudo mkswap /dev/vgkubuntu/swap_1
sudo swapon /dev/vgkubuntu/swap_1
```

Because I was careful NOT to change the LV name from the prior name, you don't need to modify the /etc/fstab file, assuming the swap device is the same and not based on a UUID.  UUIDs are great for computers, but they suck for humans.  You can check the fstab line with "swap" in it and see if it is using a UUID-based name/link or not.  If it isn't, then all should be fine after the next reboot and that's that.

I prefer to mount stuff in the /etc/fstab using LV names or LABELs, and only use UUIDs when there isn't any other good, permanent, choice.
For example, my swap line in the fstab looks like:
```
/dev/vg01/swap01     none             swap sw 0 0

```
```
$ ls -al /dev/vg01/swap01 
lrwxrwxrwx 1 root root 7 Apr 16 00:09 /dev/vg01/swap01 -> ../dm-6

``` shows that device as a link to the less useful, dynamic, device file dm-6, which can change at every reboot.  OTOH, /dev/vg01/swap01  will always, ALWAYS, point to the correct device thanks to the mapper service.

I really hope you reduce the size of your "root" LV and split things out as I've showed.  It is important to have at least 20% of the storage on the OS SSD unused.  More provides flexibility with LVM, since adding space directly where it is needed for ext4 file systems is really 1 command and trivial, but only if other LVs haven't already taken the space.

---

### Post by donald187 on 2024-04-17
Looks like they solved it with a swap file.

[https://forums.debian.net/viewtopic.php?t=158889](https://forums.debian.net/viewtopic.php?t=158889)

---

