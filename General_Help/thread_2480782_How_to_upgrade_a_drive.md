---
title: "How to upgrade a drive"
date: 2022-11-09
forum: General Help
---

### Post by satimis on 2022-11-09
Hi all,

What will be an easy way to upgrade a drive because of shortage in space.

**[COLOR="#FF0000"]Config of PC[/COLOR]**
**drive-1** : running Ubuntu 22.04 as host and Oracle VirtualBox
(1TB PCIe Gen 3x4 SSD, almost full leaving only about 30G space behine)
**drive-2** : running Ubuntu 22.04 as host and KVM
**drive-3** : running Windows11
**drive-4** : 4TB solely for storage of data, without OS installed

I have purchased a 2TB PCIe Gen 3x4 SSD ready to replace drive-1

Now I'm searching for an easy way to clone/duplicate drive-1 on the new 2TB PCIe Gen 3x4 SSD.  

On Internet searching I found;
**How to Clone Your Linux Hard Drive: 4 Methods**
[https://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/](https://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/)

Can I use ONE of the suggested methods?

If YES, I'll disconnect drive-3 and drive-4.  Install the new 2TB PCIe Gen 3x4 SSD (There are 2 M2(shocket3) on the motherboard).  Run Ubuntu 22.04 on drive-2 to do the job.

Which method shall I use?

Please advise.  Thanks in advance.

Regards

---

### Post by &amp;KyT$0P# on 2022-11-10
I didn't use any of the methods described in that link for my last drive upgrade.  I used GParted to: create a GUID partition table (gpt) on the target drive, copy the individual partitions from old drive to new drive (and resize them to fill the new drive as desirable), and set new filesystem UUIDs where applicable to avoid duplicated UUIDs.  Then manually, outside of GParted, updated the affected system's [FONT=Courier New]/etc/fstab[/FONT] to point to the new UUIDs before booting back into it.

Don't remember if I also needed to de-duplicate partition UUIDs, but if so, I wouldn't have done that in GParted, I would have used [FONT=Courier New]gdisk[/FONT] following [this method]("https://askubuntu.com/questions/1250224/how-to-change-partuuid/1250232#1250232").

I would recommend making a full system backup before doing this or any other method of copying/moving data to the new drive.

> **satimis said:**
> I'll disconnect drive-3 and drive-4.  Install the new 2TB PCIe Gen 3x4 SSD (There are 2 M2(shocket3) on the motherboard).  Run Ubuntu 22.04 on drive-2 to do the job.

That should be fine if your drive-2 Ubuntu installation does not mount any of the partitions on other drives via [FONT=Courier New]/etc/fstab[/FONT] or any other method that *requires* the other partitions to be available and mounted at boot time.

---

### Post by TheFu on 2022-11-10
If you used LVM2, then use the 'pvmove' command.

---

### Post by satimis on 2022-11-10
> **TheFu said:**
> If you used LVM2, then use the 'pvmove' command.
Hi,


$ lsblk```

......
......
loop21   7:21   0 260.7M  1 loop /snap/kde-frameworks-5-core18/32
loop22   7:22   0 295.7M  1 loop /snap/vlc/2344
loop23   7:23   0 320.4M  1 loop /snap/vlc/3078
sda      8:0    0   3.6T  0 disk 
&#9492;&#9472;sda1   8:1    0   3.6T  0 part /media/satimis/786a6a67-06f5-428f-a24d-fe75cd0b08d5
sdb      8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1   8:17   0   450M  0 part 
&#9500;&#9472;sdb2   8:18   0    99M  0 part 
&#9500;&#9472;sdb3   8:19   0    16M  0 part 
&#9500;&#9472;sdb4   8:20   0 929.9G  0 part 
&#9500;&#9472;sdb5   8:21   0   518M  0 part 
&#9492;&#9472;sdb6   8:22   0   516M  0 part 
sdc      8:32   0 465.8G  0 disk 
&#9500;&#9472;sdc1   8:33   0   512M  0 part 
&#9492;&#9472;sdc2   8:34   0 465.3G  0 part 
sdd      8:48   1     0B  0 disk 
nvme0n1
&#9474;      259:0    0 953.9G  0 disk 
&#9500;&#9472;nvme0n1p1
&#9474;      259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2
       259:2    0 953.4G  0 part 
  &#9500;&#9472;ubuntu--vg-root
  &#9474;    253:0    0 930.4G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1
       253:1    0   976M  0 lvm  [SWAP]

```

$ sudo fdisk -l | grep nvme0n1```

Disk /dev/nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624 2000408575 1999357952 953.4G Linux LVM

```

It is LVM not LVM2

Regards

---

### Post by satimis on 2022-11-10
> **halogen2 said:**
>  - snip -
That should be fine if your drive-2 Ubuntu installation does not mount any of the partitions on other drives via [FONT=Courier New]/etc/fstab[/FONT] or any other method that *requires* the other partitions to be available and mounted at boot time.
There is no partition on this old 1TB SSD

Only Ubuntu 22.04 installed on it as Host of VirtualBox and VirtualBox

Also several graphic editing software on this Drive

[B][COLOR="#FF0000"]Edit-1
===[/COLOR][/B]
Run dd command is the easiest way.  In my case, can I do it ?

[B][COLOR="#FF0000"]Edit-2
====[/COLOR][/B]
Just found following links;

**[COLOR="#FF0000"]Running Out of Space? How to Clone Your Linux System Drive to a Larger SSD With CloneZilla[/COLOR]**
[https://www.makeuseof.com/running-out-of-space-how-to-clone-your-linux-system-drive-to-a-larger-ssd-with-clonezilla/](https://www.makeuseof.com/running-out-of-space-how-to-clone-your-linux-system-drive-to-a-larger-ssd-with-clonezilla/)

**2 methods**
dd
CloneZilla

CloneZilla is on repo

**[COLOR="#FF0000"]How to Easily Clone and Restore a Linux Disk Image With dd[/COLOR]**
[https://www.makeuseof.com/tag/easily-clone-restore-linux-disk-image-dd/](https://www.makeuseof.com/tag/easily-clone-restore-linux-disk-image-dd/)


Regards

---

### Post by TheFu on 2022-11-10
> **satimis said:**
> It is LVM not LVM2

Regards

Then 'pvmove' will work.

```
$ man pvmove: 
NAME
       pvmove - Move extents from one physical volume to another

```
Just need both storage devices connected at the same time. When done, remove the old one. Bob's your uncle.  While the pvmove is happening, you can keep using the system.  LVM rocks!

As for moving the EFI partition to new storage, I'd use gparted.

I'm 99% certain this will "just work" and you'll be loving LVM.  Plus, you don't need to screw with the /etc/fstab, since LV names won't change.
But, if you do commonly have problems with completely understanding storage stuff, best to ensure you have backups of everything before starting.  I've used pvmove a few times. I've been shocked at how easy it is using 1 little command.  

Some recipes: [https://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](https://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)   Any LVM guide, regardless of the distro, is fine. LVM is LVM is LVM.

---

### Post by satimis on 2022-11-11
> **TheFu said:**
> Then 'pvmove' will work.

```
$ man pvmove: 
NAME
       pvmove - Move extents from one physical volume to another

```
Just need both storage devices connected at the same time. When done, remove the old one. Bob's your uncle.  While the pvmove is happening, you can keep using the system.  LVM rocks!

As for moving the EFI partition to new storage, I'd use gparted.

I'm 99% certain this will "just work" and you'll be loving LVM.  Plus, you don't need to screw with the /etc/fstab, since LV names won't change.
But, if you do commonly have problems with completely understanding storage stuff, best to ensure you have backups of everything before starting.  I've used pvmove a few times. I've been shocked at how easy it is using 1 little command.  

Some recipes: [https://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](https://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)   Any LVM guide, regardless of the distro, is fine. LVM is LVM is LVM.
Hi,

Thanks for your advice.

Searching on my PC database I found 2 years ago running dd command to clone a 500G SATA3 SSD onto a 1TB SATA3 SSD.

Now I try your suggestion to learn something new to me.

Perform follow steps;

1. Install the new 2TB NVMe SSD
2. Start drive-2 (running Ubuntu 22.04 as host and KVM)
3. On Terminal run;
$ lsblk ```

....
....
loop14   7:14   0   284K  1 loop /snap/snapd-desktop-integration/14
sda      8:0    0   3.6T  0 disk 
&#9492;&#9472;sda1   8:1    0   3.6T  0 part /media/satimis/786a6a67-...............
sdb      8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1   8:17   0   450M  0 part 
&#9500;&#9472;sdb2   8:18   0    99M  0 part 
&#9500;&#9472;sdb3   8:19   0    16M  0 part 
&#9500;&#9472;sdb4   8:20   0 929.9G  0 part /media/satimis/BA80554280550673
&#9500;&#9472;sdb5   8:21   0   518M  0 part 
&#9492;&#9472;sdb6   8:22   0   516M  0 part 
sdc      8:32   0 465.8G  0 disk 
&#9500;&#9472;sdc1   8:33   0   512M  0 part /boot/efi
&#9492;&#9472;sdc2   8:34   0 465.3G  0 part /
nvme1n1
&#9474;      259:0    0 953.9G  0 disk 
&#9500;&#9472;nvme1n1p1
&#9474;      259:1    0   512M  0 part 
&#9492;&#9472;nvme1n1p2
       259:2    0 953.4G  0 part 
  &#9500;&#9472;ubuntu--vg-root
  &#9474;    253:0    0 930.4G  0 lvm  /media/satimis/ef229efa-3019-4ba9-bddc-88c399244e99
  &#9492;&#9472;ubuntu--vg-swap_1
       253:1    0   976M  0 lvm  
nvme0n1
       259:3    0   1.8T  0 disk 

```

$ sudo dd if=/dev/nvme1n1 of=/media/satimis/786a6a67-............./1tb_ssd_backup.img```

2000409264+0 records in
2000409264+0 records out
1024209543168 bytes (1.0 TB, 954 GiB) copied, 6362.83 s, 161 MB/s

```

To create a backup.img

$ ls -l --block-size=G /media/satimis/786a6a67-.............../1tb_ssd_backup.img```

-rw-r--r-- 1 root root 954G Nov 11 22:58 /media/satimis/786a6a67-,,,,,,,,,,,,,,,,,,,,,,,,/1tb_ssd_backup.img

```

It took about 95min to finish.

Again on Terminal;
$ sudo pvmove /dev/nvme1n1 /dev/nvme0n1```

  Failed to find physical volume "/dev/nvme1n1".
  Run `pvmove --help' for more information.

```
  
I'm stuck here.  I don't understand;```

Failed to find physical volume "/dev/nvme1n1".

```

Please help.

Regards

Edit
===
1.  Do I need to format the new 2TB NVMe SSD ?
2.  Can I start the old 1TB NVMe SSD to create backup,img ?  Also to clone it to the new 2TB NVme SSD?

---

### Post by TheFu on 2022-11-11
> **satimis said:**
>  

Please help.
 

Did you click the link with recipes and follow those instructions?

---

### Post by Dennis N on 2022-11-11
> $ sudo pvmove /dev/nvme1n1 /dev/nvme0n1
Code:

  Failed to find physical volume "/dev/nvme1n1".
  Run `pvmove --help' for more information.

I'm stuck here. I don't understand;

That's not a physical volume. From your display, nvme1n1p2 is the only physical volume I can see there.

You can use **sudo pvs** to list the physical volumes and the volume group (if any) they belong to.

On this computer: 
```
[dmn@Sydney ~]$ sudo pvs
  PV             VG       Fmt  Attr PSize    PFree  
  /dev/nvme0n1p2 sn500_vg lvm2 a--  <244.14g  19.53g
  /dev/nvme0n1p3 sn500_vg lvm2 a--   117.18g <78.12g
  /dev/sda3      os_vg2   lvm2 a--   117.18g  30.68g
  /dev/sda4      os_vg2   lvm2 a--   117.18g <31.25g

```

---

### Post by satimis on 2022-11-11
According to 
13.5.2.1. Prepare the disk
of the link recipes

$ sudo pvcreate /dev/nvme0n1```

  Physical volume "/dev/nvme0n1" successfully created.

```

$ sudo vgextend dev /dev/nvme0n1```

  Volume group "dev" not found
  Cannot process volume group dev

```

$ sudo pvs```

  PV             VG        Fmt  Attr PSize    PFree  
  /dev/nvme0n1             lvm2 ---    <1.82t  <1.82t
  /dev/nvme1n1p2 ubuntu-vg lvm2 a--  <953.37g <22.05g

```

$ sudo pvmove /dev/nvme1n1p2 /dev/nvme0n1```

  Physical Volume "/dev/nvme0n1" not found in Volume Group "ubuntu-vg".

```

Can't proceed further

Regards

[B][COLOR="#FF0000"]Edit-1
====[/COLOR][/B]
$ sudo vgextend ubuntu-vg /dev/nvme0n1```

  Volume group "ubuntu-vg" successfully extended

```

$ sudo pvmove /dev/nvme1n1p2 /dev/nvme0n1```

  /dev/nvme1n1p2: Moved: 0.01%
  /dev/nvme1n1p2: Moved: 1.49%
  /dev/nvme1n1p2: Moved: 3.04%
  /dev/nvme1n1p2: Moved: 4.57%
...

```

Now it is working.  I have to wait until it finishes

[B][COLOR="#FF0000"]Edit-2
====[/COLOR][/B]
Now it finishes. taking 25min to complete

```

....
  /dev/nvme1n1p2: Moved: 60.53%
  /dev/nvme1n1p2: Moved: 62.11%
  /dev/nvme1n1p2: Moved: 63.68%
  /dev/nvme1n1p2: Moved: 91.33%
  /dev/nvme1n1p2: Moved: 95.97%
  /dev/nvme1n1p2: Moved: 99.90%
  /dev/nvme1n1p2: Moved: 100.00%

```

$ lsblk```

......
......
loop13                7:13   0    48M  1 loop /snap/snapd/17336
loop14                7:14   0   284K  1 loop /snap/snapd-desktop-integration/14
sda                   8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1                8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2                8:2    0 465.3G  0 part /
nvme1n1             259:0    0 953.9G  0 disk 
&#9500;&#9472;nvme1n1p1         259:1    0   512M  0 part 
&#9492;&#9472;nvme1n1p2         259:2    0 953.4G  0 part 
nvme0n1             259:3    0   1.8T  0 disk 
&#9500;&#9472;ubuntu--vg-root   253:0    0 930.4G  0 lvm  
&#9492;&#9472;ubuntu--vg-swap_1 253:1    0   976M  0 lvm  

```

[B][COLOR="#FF0000"]Edit-3
====[/COLOR][/B]
Reboot PC to BIOS

On BIOS I can't find this new 2TB NVMe SSD to boot

It is very strange to me.

Any help?  Thanks

---

### Post by TheFu on 2022-11-11
Ah, I see that you've figured out that you cannot simply copy/paste commands. They need to be modified for YOUR situation.  dev ---> {whatever your VG is called}

Did you move/handle the non-LVM partitions?  Seems those would need to be moved and the fstab would need to be updated for any changes to UUIDs.
Did you tell the boot loader (grub or EFI) about the new boot area?  For grub, that usually means running 'sudo update-grub'.  I don't know how to tell EFI about it, perhaps efibootmgr? IDK.
```
NAME
       efibootmgr - manipulate the UEFI Boot Manager

DESCRIPTION
       efibootmgr is a userspace application used to modify the UEFI Boot Man&#8208;
       ager. This application can create and destroy boot entries, change  the
       boot order, change the next running boot option, and more.

```

Did you tell the BIOS which device to boot from too?  If the new storage isn't where the old storage was, it probably won't be found.

But you do have to admit that pvmove was freakin' easy, right?

---

### Post by satimis on 2022-11-11
> **TheFu said:**
> Ah, I see that you've figured out that you cannot simply copy/paste commands. They need to be modified for YOUR situation.  dev ---> {whatever your VG is called}

Did you move/handle the non-LVM partitions?  Seems those would need to be moved and the fstab would need to be updated for any changes to UUIDs.
Did you tell the boot loader (grub or EFI) about the new boot area?  For grub, that usually means running 'sudo update-grub'.  I don't know how to tell EFI about it, perhaps efibootmgr? IDK.
```
NAME
       efibootmgr - manipulate the UEFI Boot Manager

DESCRIPTION
       efibootmgr is a userspace application used to modify the UEFI Boot Man&#8208;
       ager. This application can create and destroy boot entries, change  the
       boot order, change the next running boot option, and more.

```

Did you tell the BIOS which device to boot from too?  If the new storage isn't where the old storage was, it probably won't be found.

But you do have to admit that pvmove was freakin' easy, right?
Hi,

Thanks for your advice.

I have been porkering around on BIOS.  The boot options can't find the new 2TB NVMe Gen 3 SSD.

Any suggestion ?

From the Database of my PC I found one dd command complete the job;
```

dd if=/dev/sdX of=/dev/sdY bs=64K conv=noerror,sync

```
I did it before years ago, upgrading a SATA3 500G SSD to a SATA 1TB SSD

Regards

---

### Post by TheFu on 2022-11-11
Upgrade the BIOS and the new stroage firmware.  If the BIOS doesn't see the SSD, that's a pretty big issue.
If you use that dd command, it will break the pvmove work done already.  Also, that block size seems a bit small for any drives these days.

BTW, the plain 'lsblk' without options isn't nearly as good as the commands we all post in these forums with 5+ options.  I use:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
but if you need to know the UUIDs, then add that to the end of the option list.

---

### Post by satimis on 2022-11-11
> **TheFu said:**
> Upgrade the BIOS and the new stroage firmware.  If the BIOS doesn't see the SSD, that's a pretty big issue.
If you use that dd command, it will break the pvmove work done already.  Also, that block size seems a bit small for any drives these days.

BTW, the plain 'lsblk' without options isn't nearly as good as the commands we all post in these forums with 5+ options.  I use:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
but if you need to know the UUIDs, then add that to the end of the option list.
$ alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'

No output

$ lsblk -e 7 -o name,size,type,fstype,mountpoint```

NAME          SIZE TYPE FSTYPE  MOUNTPOINT
sda           3.6T disk         
&#9492;&#9472;sda1        3.6T part ext4    /media/satimis/786a6a67-06f5-428f-a24d-fe75cd0b0
sdb         931.5G disk         
&#9500;&#9472;sdb1        450M part ntfs    
&#9500;&#9472;sdb2         99M part vfat    
&#9500;&#9472;sdb3         16M part         
&#9500;&#9472;sdb4      929.9G part ntfs    
&#9500;&#9472;sdb5        518M part ntfs    
&#9492;&#9472;sdb6        516M part ntfs    
sdc         465.8G disk         
&#9500;&#9472;sdc1        512M part vfat    /boot/efi
&#9492;&#9472;sdc2      465.3G part ext4    /
sr0          1024M rom          
nvme0n1     953.9G disk         
&#9500;&#9472;nvme0n1p1   512M part vfat    
&#9492;&#9472;nvme0n1p2 953.4G part LVM2_me 
nvme1n1       1.8T disk LVM2_me 
&#9500;&#9472;ubuntu--vg-root
&#9474;           930.4G lvm  ext4    
&#9492;&#9472;ubuntu--vg-swap_1
              976M lvm  swap    

```

---

### Post by Dennis N on 2022-11-11
> On BIOS I can't find this new 2TB NVMe SSD to boot... Any help? Thanks 

Well, I think the EFI system partition for the OS you moved to the 2TB drive is still on the other NVME drive. The boot loader is still directed to the original location. If there is no valid path for booting the OS, you may not see the OS as a UEFI boot menu entry.

---

### Post by satimis on 2022-11-11
> **Dennis N said:**
> Well, I think the EFI system partition for the OS you moved to the 2TB drive is still on the other NVME drive. The boot loader is still directed to the original location. If there is no valid path for booting the OS, you may not see the OS as a UEFI boot menu entry.
I have tried removing the old 1TB NVME SSD and install the new 2TB NVME on its M.2 socket.  Still the BIOS can't find it.

Any solution?  Thanks

---

### Post by Dennis N on 2022-11-12
First, a comment:
You used the entire disk for your new physical volume. That's possible, but usually you use disk partitions for making physical volumes.  

As to your question:
> I have tried removing the old 1TB NVME SSD and install the new 2TB NVME on its M.2 socket. Still the BIOS can't find it.
Any solution? Thanks 

I don't understand the question here. Certainly your UEFI knows your drive is there, since you did some operations with the new drive.

Your display shows another drive sdc that appears to have an OS. Does the grub menu of that OS detect the new OS on the 2 TB after you run update-grub?

Also, you might be able to use the boot repair CD to reinstall grub to fix your booting - I don't know for sure since I have never used it, and don't know where you get it. Someone else will have to advise you on that and its use.

---

### Post by Dennis N on 2022-11-12
Just thinking - another option would be to reverse the pvmove and everything will go back as it was. Then rethink how you want to do this.

---

### Post by satimis on 2022-11-12
> **Dennis N said:**
> First, a comment:
You used the entire disk for your new physical volume. That's possible, but usually you use disk partitions for making physical volumes.  

As to your question:


I don't understand the question here. Certainly your UEFI knows your drive is there, since you did some operations with the new drive.

Your display shows another drive sdc that appears to have an OS. Does the grub menu of that OS detect the new OS on the 2 TB after you run update-grub?

Also, you might be able to use the boot repair CD to reinstall grub to fix your booting - I don't know for sure since I have never used it, and don't know where you get it. Someone else will have to advise you on that and its use.
I haven't done anything on the new 2TB NVMe SSD after its purchase.  I just plug it on M.2-2 socket and start cloning the old 1TB NVMe SSD on it.  

There are 2 M.2 sockets on Asus motherboard.  The old 1 TB NVMe SSD is pluged on M.2-1 socket

I use the entire new 2TB NVMe SSD without partition.

I plug the new 2TB new NVMe SSD on M.2-1 socket to check whether it can be detected by BIOS but NO

There are 5 hdd on this PC

sda : 4TB WD hdd solely for data storage without OS installed
sdb : 1TB SSD running Windows 11
sdc : 500G SSD running Ubuntu and KVM

I ran pvmove on sdc for cloning

nvme1n1 : the old 1TB NVMe SSD
nvme0n1 ; the new 2TB NVMe SSD

Now I have replugin all hdds.  
```

sda                   8:0    0   3.6T  0 disk 
&#9492;&#9472;sda1                8:1    0   3.6T  0 part 
sdb                   8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1                8:17   0   450M  0 part 
&#9500;&#9472;sdb2                8:18   0    99M  0 part 
&#9500;&#9472;sdb3                8:19   0    16M  0 part 
&#9500;&#9472;sdb4                8:20   0 929.9G  0 part 
&#9500;&#9472;sdb5                8:21   0   518M  0 part 
&#9492;&#9472;sdb6                8:22   0   516M  0 part 
sdc                   8:32   0 465.8G  0 disk 
&#9500;&#9472;sdc1                8:33   0   512M  0 part 
&#9492;&#9472;sdc2                8:34   0 465.3G  0 part 
sr0                  11:0    1  1024M  0 rom  
nvme1n1             259:0    0 953.9G  0 disk 
&#9500;&#9472;nvme1n1p1         259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme1n1p2         259:2    0 953.4G  0 part 
nvme0n1             259:3    0   1.8T  0 disk 
&#9500;&#9472;ubuntu--vg-root   253:0    0 930.4G  0 lvm  /
&#9492;&#9472;ubuntu--vg-swap_1 253:1    0   976M  0 lvm  [SWAP]

```

BIOS can detect only sdb, sdc, nvme1n1 but not sda and nvme0n1

I don't have repair CD.  I have Ubuntu 22.04 USB installer.  Can I use it to reinstall grub?  If YES please advise HOW?

---

### Post by satimis on 2022-11-12
> **Dennis N said:**
> Just thinking - another option would be to reverse the pvmove and everything will go back as it was. Then rethink how you want to do this.
I think the easy solution for me is to run "dd" cloning the old 1TB NVMe SSD on the new 2TB NVMe SSD.

My aim to continue this posting is SOLELY to learn.

I'm now looking at;
Boot-Repair
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Edit
==
Even cloning fails, in the worst case.  I can install Ubuntu 22.04 desktop on the new 2TB NVMe SSD running USB installer and copy all data from old 1TB NVMe SSD on it.  I have already copied all data of the old 1TB NVMe SSD onto the 4TB storage disk

---

### Post by satimis on 2022-11-12
Hi all,

Something terrible happens to the old 1TB NVMe SSD.  It is now unable to boot, displaying a dark screen showing;

grub>

I just discover it.  Please advise how to fix the problem.

Shall I start a new posting?

Regards

---

### Post by Dennis N on 2022-11-12
From your display (post 19) showing the 2 NVMe drives:
```
nvme1n1             259:0    0 953.9G  0 disk 
&#9500;&#9472;nvme1n1p1         259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme1n1p2         259:2    0 953.4G  0 part 
nvme0n1             259:3    0   1.8T  0 disk 
&#9500;&#9472;ubuntu--vg-root   253:0    0 930.4G  0 lvm  /
&#9492;&#9472;ubuntu--vg-swap_1 253:1    0   976M  0 lvm  [SWAP]
```

If this is the system after moving the PV, it looks like you were using Ubuntu on the 2 TB drive when generating this output. It works. Isn't that what you want to achieve?

Comments:
The ESP for the OS on the 2 TB drive is on the 1 TB drive. That's OK, but both drives must be present for the OS to boot.
This situation a bit unusual in that there are no partitions on the 2 TB drive. In effect, the entire drive works as the partition.
 There is no longer an OS on the 1 TB NVMe to boot.
 
What needs to be done?

---

### Post by TheFu on 2022-11-12
I never expected something so easy to become so hard, especially for people with 15+ yrs experience.  This isn't the first time.  Sorry.  Seems I'm not helping.

---

### Post by mIk3_08 on 2022-11-12
> **satimis said:**
> I think the easy solution for me is to run "dd" cloning the old 1TB NVMe SSD on the new 2TB NVMe SSD.

My aim to continue this posting is SOLELY to learn.

I'm now looking at;
Boot-Repair
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Edit
==
Even cloning fails, in the worst case.  I can install Ubuntu 22.04 desktop on the new 2TB NVMe SSD running USB installer and copy all data from old 1TB NVMe SSD on it.  I have already copied all data of the old 1TB NVMe SSD onto the 4TB storage disk
so far in my experienced in cloning the system it will be best to use clonezilla that is why I recommend clonezilla for best result so far. I already used it many times and I haven't encountered any errors during the process of my system back up. Actually, it is very handy to use and just be careful for it but If you find not too easy to use then use what is best and more easy for you. Regards cheers

---

### Post by satimis on 2022-11-13
> **mIk3_08 said:**
> so far in my experienced in cloning the system it will be best to use clonezilla that is why I recommend clonezilla for best result so far. I already used it many times and I haven't encountered any errors during the process of my system back up. Actually, it is very handy to use and just be careful for it but If you find not too easy to use then use what is best and more easy for you. Regards cheers
Hi mIk3_08,

Thanks for your advice.  Unfortunately it comes too late.  I ran the wrong tool to do the job causing me lot of trouble.  Fortunately I have fixed the problem.  Please refer to my next posting.
[B][COLOR="#FF0000"]
clonezilla is on repo[/COLOR][/B]

Regards

---

### Post by satimis on 2022-11-13
Hi all,

**[COLOR="#FF0000"]Problem solved.[/COLOR]**

Fortunately before starting my adventure I ran dd command to backup the entire old 1TB NVME SSD and save the backup image on a storage drive of the PC. After running 'pvmove' to clone the old 1TB NVME SSD onto the new 2TB NVME SSD, both SSDs are unable to be detected by the BIOS of motherboard. After searching around without solution I decide  running dd command to restore the aforesaid image on the new 2TB NVME SSD;

```

$ sudo dd if=/path/to/backup.img of=/dev/nvme0n1 bs=64

```

Installation went through without complaint.  After finish the BIOS can detect only the new 2TB NVME SSD but it can only boot to grub> command line screen.  Later I found out that after removing the old 1TB NVME SSD from PC the new 2TB NVME can boot to GRUB menu then straight to Ubuntu 22.04 desktop

I suppose the system on the old 1TB NVME SSD has been damaged during cloning.  I won't repair it and use it installing other OS.

Regards

[B][COLOR="#FF0000"]Edit-1
====[/COLOR][/B]
To upgrade a drive by cloning because of running shot of disc space is NOT a good idea.  It is better do a clean installation.

**Problem-1**
All VMs have to change "Network Settings" before they can be started

Now I'm copying all working data on the new 2TB NVME SSD to the storage drive, in particular the VM images on "VirtualBox VM" folder.  I'm prepared to do a clean installation later

---

