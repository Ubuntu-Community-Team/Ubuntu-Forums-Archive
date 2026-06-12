---
title: "Install with 2 drive RAID 1, I did it but is there an easier way?"
date: 2023-06-04
forum: General Help
---

### Post by funkytwig4 on 2023-06-04
I am seting up a server that has 2 drives in it that I want to setup as RAID 1.  

If I use the "Create Software RAID (md)" option and select both my disks the installer tells me: "If you put all disks into RAIDS or LVM VGs, there will be nowhere to put the boot partition."

I did this years ago and it was easy.  I just said format as RAID and set it as RAID 1. 

Below is what I ended up doing.  There were around 30 individual manual steps (using staps from [https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices](https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices)).

Am I missing something.  A server with 2 drives in RAID 1 seems a fairly standard use case for a small server (it was a backup server).
Ben


[IMG]https://tvpp.tv/wp-content/uploads/2023/06/raid_serup-scaled.jpg[/IMG]

---

### Post by TheFu on 2023-06-04
Ubuntu's Server installer has always sucked at RAID stuff.  I suspect your memory for it being easy was with a different distro.  For example, CentOS had a nice installer that handled RAID and LVM nicely.  Ubuntu's installers have always been bad at non-standard disk layouts.  What I do is start the installer, switch to a different tty, install ssh, pull over some disk setup scripts and get it all setup they way I want from outside the installer.  Then switch back to the installer and choose "do something else" in the disk areas and point the different, known, mount locations at the specific storage objects I've setup.

BTW, if it were me, I'd have only 2 mdadm arrays and use LVM on-top of the 2nd, larger, array for the added flexibility.  YMMV.
The easiest way to setup RAID1 is to not use mdadm, only use LVM and choose the default LVM layout with 1 disk.  Post install, add the other disk to the VG and create LV mirrors of existing LVs.  The results look like this:
```
$ lsblk -e 7 -o name,size,type,fstype,label,mountpoint
NAME                       SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                         15G disk                   
&#9500;&#9472;vda1                       1M part                   
&#9500;&#9472;vda2                     768M part ext4              /boot
&#9492;&#9472;vda3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_0     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9500;&#9472;vg--00-lv--0_rimage_0   10G lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap          1G lvm  swap              [SWAP]
vdb                         15G disk                   
&#9500;&#9472;vdb1                       1M part                   
&#9500;&#9472;vdb2                     768M part                   
&#9492;&#9472;vdb3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_1     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--0_rimage_1   10G lvm                    
    &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /

$ sudo pvs
  PV         VG    Fmt  Attr PSize   PFree
  /dev/vda3  vg-00 lvm2 a--  <13.25g 2.24g
  /dev/vdb3  vg-00 lvm2 a--  <13.25g 3.24g

$ sudo vgs
  VG    #PV #LV #SN Attr   VSize  VFree
  vg-00   2   2   0 wz--n- 26.49g 5.48g

$ sudo lvs
  LV      VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0    vg-00 rwi-ao**r**--- 10.00g                                    100.00          
  lv-swap vg-00 -wi-ao----  1.00g     
```
Pretty ugly, but it is mirrored.  I don't mirror swap.
vda2 isn't active-active mirrored.  I have to manually mirror it to vdb3 after kernel updates.  This VM is legacy boot, not EFI.  The ugliness of LVM mirror has me running away, back to mdadm+LVM.

But LVM-only mirrors are "easier" to install.  That doesn't mean it is a good idea, however.

---

### Post by funkytwig4 on 2023-06-04
Thanks for that but I only do it a cople of times a decase so will stick with manual step.  It was defenatly ubuntu, its the machine I am decomisioning and replacing with the one I am setting up.

---

### Post by TheFu on 2023-06-04
> **funkytwig4 said:**
> Thanks for that but I only do it a cople of times a decase so will stick with manual step.  It was defenatly ubuntu, its the machine I am decomisioning and replacing with the one I am setting up.

The new hotness is ZFS.

---

### Post by #&amp;thj^% on 2023-06-04
> **TheFu said:**
> The new hotness is ZFS.

+1
But comes with a learning curve.
I remember with 18.04 I hated it, Now days it's my preferred storage solution.:) 
Works quite nicely with KVM's as well.
Sorry for the drive by and TheFu has given you some very wise advice.

---

### Post by TheFu on 2023-06-04
> **1fallen said:**
>  
Sorry for the drive by and TheFu has given you some very wise advice.

This time, I don't really have much wisdom.  

RAID1 setups should be much easier on a Server OS install. We shouldn't have to do anything besides check a box like we do with LVM.  The installer should "do the right thing" with mdadm and LVM, since nobody uses mdadm without LVM the last 15 yrs. It just isn't done.
I suspect most enterprises use something like Cobbler to lay down their storage in a reproducible way with automatic installs for their VM hosts.  For VMs, nobody sets up RAID **inside** the VM, unless they are playing.  The host or back end storage should handle RAID levels seamlessly so the guests don't know anything about it.

Since 2005, everywhere I worked didn't allow installing applications directly onto physical hardware. It has all been virtual machines or containers all this time.

---

### Post by SeijiSensei on 2023-06-04
I usually create a small partition for boot/root on each drive, then allocate the rest of the drive to RAID1. I mount the array as /home.

I usually copy the boot/root partition on the first drive to a similarly-sized partition on the second as a backup.

---

### Post by funkytwig4 on 2023-06-04
> **TheFu said:**
> The new hotness is ZFS.

Yes, VMs are the way to go, and docker.  This is a very small comunity orginisation and kind of needs to be cheap and chearfull but you are 100% correct.  I havent done loads of installes, if I had I probably would as it would be easy.  We live and learn.

---

### Post by funkytwig4 on 2023-06-04
> **SeijiSensei said:**
> I usually create a small partition for  boot/root on each drive, then allocate the rest of the drive to RAID1. I  mount the array as /home.

I usually copy the boot/root partition on the first drive to a similarly-sized partition on the second as a backup.

Cunning.  Ive got to do another so will try that.  How about swap?  Hang on, so boot/root are not RAID 1 in your case?

---

### Post by funkytwig4 on 2023-06-04
> **TheFu said:**
> This time, I don't really have much wisdom.  

RAID1 setups should be much easier on a Server OS install. We shouldn't  have to do anything besides check a box like we do with LVM.  The  installer should "do the right thing" with mdadm and LVM, since nobody  uses mdadm without LVM the last 15 yrs. It just isn't done.
I suspect most enterprises use something like Cobbler to lay down their  storage in a reproducible way with automatic installs for their VM  hosts.  For VMs, nobody sets up RAID **inside** the VM, unless they are  playing.  The host or back end storage should handle RAID levels  seamlessly so the guests don't know anything about it.

Since 2005, everywhere I worked didn't allow installing applications  directly onto physical hardware. It has all been virtual machines or  containers all this time.

So true.  Wasted at leat 2 houres but it was fun (OK it was not).

---

### Post by funkytwig4 on 2023-06-04
> **TheFu said:**
> The new hotness is ZFS.

LOL, I was just reading up about that.

---

### Post by MAFoElffen on 2023-06-05
Logically, with whatever filesystem I install, I usually lay out my systems in a separated, modular manner... The basic "default install" does not lay out that way, so I end up doing all my partitioning and filesystem prep, before firing up the installer, then install into that.

For example:

/boot -- The boot drive: this allows anything to be read from the intramfs, then connected to from there.
/ -- The root drive: So that if a system failure occurs, this can be reinstalled quickly without affecting other things.
/home --Users collect things. Separated out, easy to move around in a migration or reinstall.
/data -- Network shares, databases, storage pools for my VM disk images, and ISO's for building them.
/swap and other storage caches
/backups

Those are the basic areas, I tried to separate out, even if a some are on the same storage disks. Of those, then I will do raid of those, with pool and datasets within them. (not necessarily in that order.) Of the things I do in RAID, I always do /data, then /home, maybe the root drive... My current preferences for filesystem managers are ZFS, LVM, then BTRFS. I deal with mdadm and LUKS separately in my decision process, and use then in an outer layer. ZFS is my personal preference for a file manager / filesystem.

I always use partitions for my outer storage container as the outside 'shell' = never do I install anything to a raw disk, with the disk as the container. That way I have control of where they try to write to. LVM, mdadm, and ZFS can do raw, but I have most often ran into serious troubles later doing that. 

LVM2 has the least learning curve, and can do a whole lot of things. Being able to create datasets to isolate data and system, moving things around, resizing, taking snapshots, creating and managing RAID members internally... Mostly all 'Live', on a running filesystem. People maybe scratch the surface of what it can do. That is true for other file managers and file systems as well.

But yes, the basic default installer is just a jumping off place to allow a basic install.

It can always be used to install the basic system, with a filesystem type, and expanded from there... Just another strategy.

---

### Post by SeijiSensei on 2023-06-24
> **funkytwig4 said:**
> Cunning.  Ive got to do another so will try that.  How about swap?  Hang on, so boot/root are not RAID 1 in your case?
No, boot and root are not on a RAID device. However if you duplicate that partition from one drive to the other, you'll have an emergency backup. Frankly, it doesn't much matter to me about boot/root. In the highly unlikely event I would encounter a problem, I can just reinstall Ubuntu. All my data is preserved in the RAID array attached to /home or on my server.

---

