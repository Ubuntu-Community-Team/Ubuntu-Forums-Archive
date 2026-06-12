---
title: "Ubuntu 22.04 ISO Install"
date: 2023-12-01
forum: General Help
---

### Post by box02-02 on 2023-12-01
Hi.

I'm trying to install an ubuntu 22.04 iso,  booting from a USB onto an empty 512gb SSD,  and I have some questions on the installation.

On the SSD I made a 523mb 'efi' partition and a 100gb ext4 partition.

Here is a pic of the Partitions displayed by the installer:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293144&stc=1[/IMG]

1. Does the 523mb efi partition make sense ? 

2. What should the mount point be for the ext4 partition - '/' or '/boot' ??

3. I  set the 'Device for boot loader installation' as /dev/sda. Is this correct or should it be /dev/sda1 ?

4. There is a 1mb 'Free Space' entry. Should I be doing anything with this ?? 
Here is a pic of the options asked if I click on it:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293146&stc=1[/IMG]

It asks 'use as:', so I tried 'efi' or 'device for boot loader', both  of which yield an 'unable to satisfy all constraints on the partition' error. What to do here ??

Any help will be greatly appreciated.

Thanks,
M...

---

### Post by ajgreeny on 2023-12-01
1. Yes, plenty big enough. Mine is 200M and only a small amount of that is in use by two versions of Xubuntu.

2. Set the mountpoint as / or root assuming you intend having just the one partition.

3. I think that whatever you answer thre for the bootloader installation it will go to the correct site when you install but nevertheless I recommend you simply answer /dev/sda and let the installer do its own work.

4. Ignore that 1M free space space; it is i believe a hangover from the days when partitions were arranged and partitioned in a different manner, maybe by sectors or something else about which I am no expert.  However, I have a similar 1M free space on my disk and it's impossible to remove it ; if you move all the partitions on disk to use it the same 1M free space will still be somewhere else such as at the end of the disk.

---

### Post by box02-02 on 2023-12-01
Thanks ajgreeny for the super fast and informative response.

Just one question re your: > *Set the mount point as / or root assuming you intend having just the one partition*

There will be multiple partitions on this SSD. But what do other partitions have to do with the mount point of the ext4 ubuntu partition ? 

So should I set mount point to be /boot ? Gparted shows the mount point of my active  ext4 ubuntu partition as "/", yet I have 6 other partitions.

Thanks again,
M...

---

### Post by ajgreeny on 2023-12-02
The main ext4 partition must be / and without that you will not be able to run the Linux system.
Without knowing what those other partitions are, or why you think you need them, it is impossible to answer your question properly.

Many users particularly those who are new to Linux will simply let the installer use the whole disk by choosing the default installation option.
That will automatically create a root, /, partition in which the whole system will be installed and also the EFI partition in which the grub and boot system will be installed.
As you are obviously new to all this I recommend that you keep things as simple as possible and not try to run before you can walk. Once you have used the system for a while and understand how the whole thing works you can investigate other ways of working with separate partitions.

---

### Post by yancek on 2023-12-02
>  There is a 1mb 'Free Space' entry. Should I be doing anything with this ??  

No.  It is often the case that a 1MB (sometimes larger) free space between partitions.  If your hard drive is a GPT drive and you were installing in Legacy mode, you would use that 1MB partition (unformatted) as a BIOS_boot partition.  Since you already have an EFI partition and are doing an EFI install, leave it.

Set the mount point for the partition on which you are installing Ubuntu as / as indicated in the earlier post.  Every Linux OS you install will have a / partition.  If you install 5 or more Linux systems on the same computer, even on the same physical drive, they will all have a / partition seen from the booted system.  When booted from one system, the other systems will show a different mount point when booted from that system.  Most likely, under /media/username.

>    booting from a USB onto an empty 512gb SSD

I don't know what that means.  Your gparted output shows a device with a number of partitions on it, not empty.  Doesn't look like an SSD drive.
Bootloader installation should be taken care of by the installer and you can install either to the device (/dev/sda) or the EFI partition (/dev/sda2 in your case).  The only circumstance I can think of that it would make sense to install to sda1 ( / filesystem partition) is if you had another Linux OS installed and intended to use the bootloader from that OS.  These suggestions are based on the information you posted which indicates you have only one physical drive and no other OS on the computer.  That doesn't compare with the gparted information as it clearly shows an ntfs partition on this device.   Is that a windows install or just a data partition?

---

### Post by TheFu on 2023-12-02
> **box02-02 said:**
> On the SSD I made a 523mb 'efi' partition and a 100gb ext4 partition.

Here is a pic of the Partitions displayed by the installer:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293144&stc=1[/IMG]

1. Does the 523mb efi partition make sense ? 

2. What should the mount point be for the ext4 partition - '/' or '/boot' ??

3. I  set the 'Device for boot loader installation' as /dev/sda. Is this correct or should it be /dev/sda1 ?

4. There is a 1mb 'Free Space' entry. Should I be doing anything with this ?? 
Here is a pic of the options asked if I click on it:

I'd show what I actually do, but that's probably too complex for someone new to Linux/Unix. I use LVM - Logical Volume Manager - which is a different way of managing storage, not partition-based besides using 1 partition for almost everything except the boot and EFI stuff.  Ok, just ignore the first column to see how I have setup my system(s):
```
$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint 
NAME                             TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL          MOUNTPOINT
nvme0n1                          disk                    931.5G                               
&#9500;&#9472;nvme0n1p1                      part  ext2                  1M                               
&#9500;&#9472;nvme0n1p2                      part  vfat                 50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3                      part  ext4                700M    340M    42%                /boot
&#9492;&#9472;nvme0n1p4                      part  LVM2_member       930.8G                               
  &#9500;&#9472;vg01-swap01                  lvm   swap                4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01                  lvm   ext4                 35G     25G    22%                /
  &#9500;&#9472;vg01-var01                   lvm   ext4                 20G   15.1G    17%                /var
  &#9500;&#9472;vg01-tmp01                   lvm   ext4                  4G    2.6G    28% tmp01          /tmp
  &#9500;&#9472;vg01-home01                  lvm   ext4                 20G   12.9G    30% home01         /home
  &#9492;&#9472;vg01-libvirt--01             lvm   ext4                137G    2.8G    98% libvirt--01    /var/lib/libvirt

```

Ok ... you can see the types of file systems I use, where I use them, how much I allocated, how much is used and where it is mounted.  You can think of each line as a "partition", but LVM means resizing larger is 5 seconds, on-line, trivial, and doesn't get stuck by a partition.

The fdisk output:
```
$ sudo fdisk -l /dev/nvme0n1
Disk /dev/nvme0n1: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 980 1TB                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 16384 bytes / 131072 bytes
Disklabel type: **gpt**
Disk identifier: AA2A1763-553C-4097-9CFD-D3621DFC2FE5

Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048       4095       2048     1M BIOS boot
/dev/nvme0n1p2    4096     106495     102400    50M EFI System
/dev/nvme0n1p3  106496    1540095    1433600   700M Linux filesystem
/dev/nvme0n1p4 1540096 1953525134 1951985039 930.8G Linux LVM
```
You can match up the "partitions" with the lsblk lines to see what contains which. Setting up partitions is required before doing the LVM parts, then formatting the file systems as needed.

What is also important is that the whole drive is 1TB, but I've allocated less than 250G of it, because I don't need it. Eventually, I might expand to use 80% of the SSD, but I won't use more than that.  lsblk shows how different parts of a disk are currently used. It is a very helpful, overview, command.

/boot and /boot/EFI and  / and swap are what I'd use on any system.  The other areas are negotiable based on your specific needs.  If you don't plan to have a separate /var and separate /tmp and separate /home, then an argument to add that storage up and make / of that total size could be made.  I would strongly push you to have a separate /home, however.  

The very last line is there just to show that adding storage where you need it for a specific purpose is easy.  In my example above, the 137GB area is specifically for virtual machine storage. It is actually for 1 specific, VM and sized just for it.

LVM on my system 20.04 requires that /boot and /boot/EFI be separate from /.  I think in newer releases, /boot and / can share the same area.  I'm just used to keeping them separate.

---

### Post by oldfred on 2023-12-02
If you partitioned in advance, make sure you have gpt partitioned.
UEFI wants gpt, Windows requires gpt with UEFI installs, but Ubuntu does not and it should.

I think gparted still defaults to MBR, but you can easily change to gpt.
But change with gparted totally erases drive, so backups required if drive has any data.

you can see disk label type with fdisk, parted, gdisk and gparted, if you click on view & device information.

All my installs are Kubuntu and I do not have any snaps. I can then have a bit smaller / than would be required with Ubuntu & many snap apps.
```
[FONT=monospace][COLOR=#000000]Model: Samsung SSD 970 EVO Plus 500GB (nvme) [/COLOR]
Disk /dev/nvme0n1: 500GB 
Sector size (logical/physical): 512B/512B 
[COLOR=#ff0000]Partition Table: gpt 
Disk Flags:  [/COLOR]

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  538MB   537MB   fat32        esp_nvme   boot, esp 
 2      538MB   32.0GB  31.5GB  ext4         noble 
 3      32.0GB  63.5GB  31.5GB  ext4         focal_k 
 5      63.5GB  273GB   210GB   ext4         nvme_data 
 4      469GB   500GB   31.5GB  ext4         jammy 
[/FONT]
```

---

### Post by box02-02 on 2023-12-02
Hi and thanks for all the informative responses.

yancek:
 > booting from a USB onto an empty 512gb SSD
I don't know what that means. Your gparted output shows a device with a number of partitions on it, not empty. Doesn't look like an SSD drive.

I burned an ubuntu ISO onto a usb and booted from it. The pic you see in my first post was taken by my camera during the 'install ubuntu' process, and later loaded onto my system for demonstration purposes for this post.

I pre-formated  the ssd with the efi, ext4, and multiple ntfs partitions. I did this with gparted, and uses gpt partitions.

Ultimately what I am trying to do is replicate my desktop ubuntu partition onto 3 laptops. These laptops will be windows/ubuntu dual bootable. Sadly, my old desktop is mbr, and the new laptops are gpt. I am experimenting with rsync and clonezilla to find the easiest and quickest solution.

I know I could just copy the /home directory and reinstall all the apps (many), but I'm looking for an easier way. I'd also have to deal with little things like the fact that I'm using Unity, Nemo, etc.


TheFu:
>  I'd show what I actually do, but that's probably too complex for someone new to Linux/Unix. I use LVM - Logical Volume Manager.

I've been using ubuntu since 2010. LVM sounds very interesting and I will investigate at another time.


oldfred:
>  If you partitioned in advance, make sure you have gpt partitioned.

You can see in my first post that I've allocated a 523mb fat 'efi' partition. I assume this is the 'gpt' partition that you are referring to. 

Thanks to all,
M...

---

### Post by TheFu on 2023-12-02
> **box02-02 said:**
>  

TheFu:
I've been using ubuntu since 2010. LVM sounds very interesting and I will investigate at another time.
 

Forget the LVM parts. Just use the layout - sizes, type of file systems, etc.

There are many reasons to use GPT over MBR.

Reinstalling apps isn't hard or even time consuming.  Just create a list of packages and feed that list into the installation program on the new system.  Cloning has lots of downsides, but people seem to need to learn those downsides for themselves.

A fresh install is about 12-15 minutes.
Restoring your $HOME (or all of /home/), should be 5 min, but let's say 15 minutes.
Lastly, reinstall the list of applications you made (store that list in your HOME, where you include it in your backups) - 5-15 minutes.  If you've been thinking about this more than 45 min, you've been wasting time.  The more you do it, the faster it will become.  Doing it on 3 systems isn't 3x45min.  It is more like 60 minutes total.

While I don't do it, you could setup an auto-install init file and make the first step nearly automatic.  IME, you'd need to do these installs at least 20x a year to make that worth the effort.

There are many reasons to prefer a fresh OS install. Too many to list.

---

### Post by oldfred on 2023-12-02
Creating an ESP - efi system partition does not make drive gpt or MBR.
The type of partitioning in gparted is separate & before you start to partition a drive. Default still seems to be MBR.
An install to a blank drive, will use gpt and add an ESP.
But now even an install to a MBR(msdos) drive may create an ESP, even if not used.

You can also use gparted but must change device label to gpt or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

---

### Post by box02-02 on 2023-12-03
Me Again.

I tried installing another ubuntu from the ubuntu iso usb since my first attempt failed to boot.

I left the 1mb free space alone, set the 523 mb partition to efi, and set my 100gb ubuntu partition to 'ext4' with a '/' mount point. (see my first post for a pic.)

When I tried to continue, I got "*the partition table format in use on your disk normally requires you to create a separate partition for boot loader code. This partition should be marked as 'reserved BIOS boot area' and should be at least 1mb in size. Correct the error or boot loader installation may fail.*"

I tried marking the 1mb free space entry as 'reserved BIOS boot area', but then I got a "unable to satisfy all constraints on the partition' error.

What should I do here?

Thanks,
M...

---

### Post by oldfred on 2023-12-03
If asking for a bios_grub partition you booted installer in old BIOS boot mode.
You want to boot installer in UEFI boot mode.
How you boot install media UEFI or BIOS is then how it installs.

You should have two boot options in UEFI boot menu, one clearly UEFI  as UEFI  XXX where XXX is name or label of flash drive. if entry is only XXX then that would be a BIOS boot entry.
Most tools to create flash drive create one that can be booted in either UEFI or BIOS mode. But some tools can create a BIOS on or UEFI only installer.

You want UEFI boot, not BIOS.

---

### Post by TheFu on 2023-12-04
> **box02-02 said:**
>  
I tried marking the 1mb free space entry as 'reserved BIOS boot area', but then I got a "unable to satisfy all constraints on the partition' error.

What should I do here?


I ran in to the same issues. My solution is posted in post #6.  When I finally got the partitions and labeled those partitions correct, I stopped trying.  Just look at the non-LVM partitions for examples related to UEFI booting.  That setup was an educated trial and error solution.

I'd bet oldfred's advice is more correct and will get you to the desired, fewer, partitions.

---

### Post by box02-02 on 2023-12-05
> **oldfred said:**
> If asking for a bios_grub partition you booted installer in old BIOS boot mode.
You want to boot installer in UEFI boot mode.
How you boot install media UEFI or BIOS is then how it installs.

You should have two boot options in UEFI boot menu, one clearly UEFI  as UEFI  XXX where XXX is name or label of flash drive. if entry is only XXX then that would be a BIOS boot entry.
Most tools to create flash drive create one that can be booted in either UEFI or BIOS mode. But some tools can create a BIOS on or UEFI only installer.

You want UEFI boot, not BIOS.

Hey oldfred you are bang on!

I reflashed the ubuntu ISO using Etcher and resinstalled ubuntu. It boots and all is well.

Thanks to all for your help.

M...

---

