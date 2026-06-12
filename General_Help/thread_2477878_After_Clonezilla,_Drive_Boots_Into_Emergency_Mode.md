---
title: "After Clonezilla, Drive Boots Into Emergency Mode"
date: 2022-08-09
forum: General Help
---

### Post by mdiemer on 2022-08-09
I recently installed Ubuntu 22.04, minimal install. I used clonezilla to make an image, which I intend to put on a new SSD. i wanted to make sure the HDD I originally installed to still booted,. in case of problems. but it didn't, it went into emergency mode. 

today I remembered that I had a m.2 PCE3 SSD hooked up during the install, and thought maybe that was the problem. Indeed, when I reconnected that, Ubuntu 22.04 booted fine. I found a thread somewhere that solved this by editing /etc/fstab. I'm not sure how to do that, and was thinking of just making a new image, this time with only the drive I was cloning hooked up. However, it would save time, as well as be a learning experience, if I could edit that file and fix it that way.

Here is the file, AFTER using clonezilla:




```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=90c3e7db-e665-4434-91f8-995e755b282b /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=B917-D3E8  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
```

how should I edit this file?

Thank you,

md

---

### Post by tea for one on 2022-08-09
> **mdiemer said:**
> today I remembered that I had a m.2 PCE3 SSD hooked up during the install, and thought maybe that was the problem. Indeed, when I reconnected that, Ubuntu 22.04 booted fine.
What does this M.2 device contain?

---

### Post by mdiemer on 2022-08-09
It has music sample libraries only. No OS. However, there is another SSD in the machine, but I had that disconnected when I made the image. today I connected both the m.2 and the SSD. Maybe I should try booting with just one, then the other connected?

---

### Post by tea for one on 2022-08-09
> **mdiemer said:**
> I Maybe I should try booting with just one, then the other connected?
Yes, worth a try. 
I am guessing that Grub is installed on a removable device.

When you have managed to reboot your original OS, can you open a terminal and provide the output:-
```
sudo parted -l
```

---

### Post by mdiemer on 2022-08-09
Thanks, here you go:

```

michael@michael-To-be-filled-by-O-E-M:~$ sudo parted -l
[sudo] password for michael: 
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   250GB  250GB  ext4


Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  538MB  537MB  primary   fat32
 2      539MB   500GB  499GB  extended
 5      539MB   258GB  257GB  logical   ext4
 6      258GB   500GB  242GB  logical   ext4
 3      500GB   500GB  537MB  primary   fat32        boot, esp


Model: WD My Passport 259F (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  3001GB  3001GB  ntfs         Basic data partition  msftdata


Model: Samsung SSD 980 500GB (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  500GB  500GB  ntfs               msftdata


michael@michael-To-be-filled-by-O-E-M:~$
```

---

### Post by tea for one on 2022-08-09
Now you have successfully booted into your original OS, please unplug/remove/unmount all drives except the one which is already booted.
Then run ```
sudo parted -l
``` so that the correct disk is identified.
Next, we can try and re-install Grub from a running system.

---

### Post by mdiemer on 2022-08-09
> **tea for one said:**
> Now you have successfully booted into your original OS, please unplug/remove/unmount all drives except the one which is already booted.
Then run ```
sudo parted -l
``` so that the correct disk is identified.
Next, we can try and re-install Grub from a running system.

OK, I unmounted the ones that were mounted. I did not unplug them, I assume you didn't want me to do that while the machine is running.

Here is the output:


```
michael@michael-To-be-filled-by-O-E-M:~$ sudo parted -l
[sudo] password for michael: 
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   250GB  250GB  ext4


Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  538MB  537MB  primary   fat32
 2      539MB   500GB  499GB  extended
 5      539MB   258GB  257GB  logical   ext4
 6      258GB   500GB  242GB  logical   ext4
 3      500GB   500GB  537MB  primary   fat32        boot, esp


Model: WD My Passport 259F (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  3001GB  3001GB  ntfs         Basic data partition  msftdata


Model: Samsung SSD 980 500GB (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  500GB  500GB  ntfs               msftdata


michael@michael-To-be-filled-by-O-E-M:~$ sudo parted -l
[sudo] password for michael: 
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   250GB  250GB  ext4


Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  538MB  537MB  primary   fat32
 2      539MB   500GB  499GB  extended
 5      539MB   258GB  257GB  logical   ext4
 6      258GB   500GB  242GB  logical   ext4
 3      500GB   500GB  537MB  primary   fat32        boot, esp


Model: WD My Passport 259F (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  3001GB  3001GB  ntfs         Basic data partition  msftdata


Model: Samsung SSD 980 500GB (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  500GB  500GB  ntfs               msftdata


michael@michael-To-be-filled-by-O-E-M:~$
```

---

### Post by tea for one on 2022-08-09
Is the original Ubuntu on [COLOR="#0000FF"]sda[/COLOR] (the first entry)?
If so, while in a booted running session, try this to re-install Grub to [COLOR="#0000FF"]sda[/COLOR]
```
sudo grub-install --efi-directory=/boot/efi /dev/sda
```

---

### Post by mdiemer on 2022-08-09
> **tea for one said:**
> Is the original Ubuntu on [COLOR=#0000FF]sda[/COLOR] (the first entry)?
If so, while in a booted running session, try this to re-install Grub to [COLOR=#0000FF]sda[/COLOR]
```
sudo grub-install --efi-directory=/boot/efi /dev/sda
```

No, it's on sdb, the second entry. (Ubuntu 22.04). However, I forgot to mention that this drive, which is a Seagate HDD, also has LXLE, based on Ubuntu 20.04. Thus, this drive has both Ubuntu 20.04 and Ubuntu 22.04. The LXLE was installed first, of course. The first entry has yet another Ubuntu, namely Ub. Studio, 20.04. sorry for such a complicated situation1. that one is on a Samsung SSD.

---

### Post by tea for one on 2022-08-09
Yes, complicated indeed - especially when extra details are subsequently revealed.

Now, I'm pretty sure that this dilemma is not the result of Clonezilla (unless you did a device-to-device clone and left both drives attached).
However, I'm now confused about what you want to do?

Why not arrange your UEFI set-up to boot your preferred drive?
Then, boot into the OS you want as priority and update-grub?

By the way, your Samsung HDD (device sdb) has old style msdos partition table and logical partitions.
I would really consider starting from scratch with gpt - much easier to manage.

---

### Post by mdiemer on 2022-08-09
I do apologize for the disorganized way I presented this. Here is why i did what I did:

I am not new to Linux (though far from expert), but i am new to doing music on Linux. I have been using Ubuntu Studio for the past 6 months or so. I thought I needed the specialized tools that it comes with. It turned out I didn't. I don't use any of the stuff, even the music-related ones. Nor the graphics and video ones. Also, Ub. St. changed to KDE with the latest version, and I like XFCE. So I decided to do a minimal Ubuntu install, but put XFCE-core on it. I prefer that to Xubuntu, because I still get the 5 year support. 

So, I'm in the process of switching from UB. ST. to Ubuntu-JJ, and it's working out really well, i was able to run Reaper for Linux, and install music libraries via wine (I'm actually having an issue with my Wine version but that's another thread of course). As a test, I decided to use an old HDD from an old computer, which has LXLE on it. So I made a double boot with LXLE and Ubuntu. If successful, my plan was to then make an image of the Ubuntu partition, and put that on its own SSD. So I made the image with Clonezilla. During the install, I only left the m.2 hooked up, since it's on a PCIe adapter and I didn't want to mess with it. However, I think I then did disconnect the m.2 drive, to make sure I didn't mistakenly put the image on it, and wipe out my music libraries.

The first thing I did after making the image was to make sure I could still boot Ubuntu. Then I was going to move on to transferring the image to a new (or possibly old) ssd. so, that's where I am now. It did not boot. I did try Rescutux and boot Repair, but neither worked. then I hit upon the thought that if I hooked up the m.2 drive, maybe that would do it. I also hooked up the small ssd with UB ST. I think I forgot about the external drive, so that was probably connected during the install, but like the m.2 I had disconnected it in preparation for the image transfer.

So, during the3 install, I think  the m.2 and the external (passport) were connected, along with the Seagate HDD with LXLE. The Samsung ssd with UB ST was disconnected. Then, after making the image, I disconnected the external and m.2 in preparation for the cloning. but I wanted to check to make sure the Ubuntu still worked. that's when the problem hit. 

Yeah, I know, too confusing. but that's what I came up with in order to try Ubuntu as a test. i didn't realize how complicated it would get.

Addendum: Re: the ssd with Ub ST on it: that ssd came out of the same computer that the old HHD was in, an old Gateway AMD dual-core, so that's why it's configured like that, i suppose...

Also, I am using bios, not uefi.

---

### Post by mdiemer on 2022-08-09
I just did some tests: First, I switched in bios to have Ubuntu as first boot drive (that is, the HDD with LXLE + Ubuntu).

1. With only the m.2 and the HDD with Ubuntu connected: boots to LXLE Grub, but Ubuntu won't boot.
2. With the m.2, the HDD and the external connected: boots to LXLE Grub, but Ubuntu won't boot.
3. With the m.2, external, the ssd with Ubuntu Studio and the HDD with Ubuntu connected: boots to LXLE Grub, Ubuntu DOES
 boot.

So it looks like the ssd with Ubuntu Studio needs to be connected for Ubuntu 22 to boot.

---

### Post by tea for one on 2022-08-10
> **mdiemer said:**
> Also, I am using bios, not uefi.
Are you sure? 
Your previous output shows ESP on two disks:-
```
[COLOR="#0000FF"]sda partition 1[/COLOR] 1049kB 538MB 537MB fat32 EFI System Partition boot, esp
[COLOR="#0000FF"]sdb partition 3[/COLOR] 500GB 500GB 537MB primary fat32 boot, esp 
```

How many operating systems do you wish to use for the future?
My instinct tells me that it may be worth considering starting from scratch because the existing situation is too difficult to follow remotely?

---

### Post by mdiemer on 2022-08-10
Well, I guess I was wrong about bios. Sorry.

I have also come to the conclusion that things have gotten way too confusing. I've decided to just do a simple dual-boot with Windows 7 and Ubuntu, on the C drive. Originally, this machine, which is a bare-bones one designed just for music creation, had 2 WD Black 1 TB hard drives, a C and D drive. I have the music libraries I use on Windows on the D drive. So now I'll have both Windows and Ubuntu on the C drive, the D drive for Windows libraries; and the m.2 for my Linux libraries. (I can't use all my Windows libraries, specifically East-West and Vienna symphonic libraries, on Linux, because they require dongles. I can't get them to work on Linux).

Although a SSD for Linux would of course be better, once the system is up and running, my projects load as fast, due to the m.2 drive which holds the libraries. and when using Windows 7, the WD drive boots quite fast, so I expect Ubuntu will too.  Those WD blacks are still good drives, as far as HDD's go.

So that's where I'm at now. My only SSD's are two 250 GB ones, with Bodhi on one in an old Gateway desktop, and Ubuntu Studio on the other, in the music machine. So I'd either have to buy a new one, or settle for a small drive, which could be OK but you never know. and my C drive has over 500GB available. I can always go with a new SSD later if necessary. but hopefully this will work out.

Addendum: And I think i will just start over, install Ubuntu the "alongside windows" way, as cloning an image is too risky. I could wipe out windows. not that I like Windows anymore. But I have a lot work invested in it.

---

### Post by oldfred on 2022-08-10
I have always preferred new clean installs. 
But you have to have good backups including a list of installed apps, and all data. And if server apps those from /.

UEFI "forget" UEFI boot entries if a drive is disconnected. You should be able to boot a drive entry that is /EFI/Boot/bootx64.efi, just like you boot live installer from a USB flash drive.

To quickly see your drives & some details see man lsblk for other fields you can show:
lsblk -e 7 -o name,fstype,size,model,fsused,label,partlabel,mountpoint

I periodically run Boot-Repair's Summary Report to document system. Copy into /home so part of backup. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And more hardware details:
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

Then you have a better understanding of what is where.

---

### Post by tea for one on 2022-08-10
Good decision to have a complete evaluation of your Operating Systems.

However, I would like to add some further comments:-
Windows 7 is unsupported and should not be used for internet access.
As you have many disks, please consider installing each OS on a separate disk.
Each OS on its own disk can be booted via UEFI boot menu (Grub difficulties should disappear).
For future-proofing, install in UEFI mode with GPT.

Make sure that you have data backups before beginning the project.

Good luck with the project.

---

### Post by mdiemer on 2022-08-12
> **oldfred said:**
> I have always preferred new clean installs. 
But you have to have good backups including a list of installed apps, and all data. And if server apps those from /.

UEFI "forget" UEFI boot entries if a drive is disconnected. You should be able to boot a drive entry that is /EFI/Boot/bootx64.efi, just like you boot live installer from a USB flash drive.

To quickly see your drives & some details see man lsblk for other fields you can show:
lsblk -e 7 -o name,fstype,size,model,fsused,label,partlabel,mountpoint

I periodically run Boot-Repair's Summary Report to document system. Copy into /home so part of backup. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And more hardware details:
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

Then you have a better understanding of what is where.

Thanks for the tips, very helpful. I'm up and running now with a good old fashioned dual boot, Ubuntu & windows 7. All other drives disconnected, except for the D drive, which is where my Windows music libraries are, and the m.2 drive, which is where my Linux music libraries are. And some external drives as needed.

What I was doing as indicated in this thread was all experimental. The main thing was to confirm that I did not need a specialized Linux OS to do my music. I was very happy to discover the minimal Ubuntu install option. Now that I have it running on my C drive, I finally have the situation I need. I will be imaging the whole C drive soon. The other drives were temporary and are not in the picture anymore.

---

### Post by mdiemer on 2022-08-12
> **tea for one said:**
> Good decision to have a complete evaluation of your Operating Systems.

However, I would like to add some further comments:-
Windows 7 is unsupported and should not be used for internet access.
As you have many disks, please consider installing each OS on a separate disk.
Each OS on its own disk can be booted via UEFI boot menu (Grub difficulties should disappear).
For future-proofing, install in UEFI mode with GPT.

Make sure that you have data backups before beginning the project.

Good luck with the project.

As indicated in the previous response, all is well at this point. Re: windows 7, when I use it I am offline by default. It cannot connect itself unless I change the settings. At this point, it may never go online again. All I need it for is to export my projects to Linux, or make final versions of those I consider finished in Windows. Those utilize orchestral libraries that I cannot use on Linux. So I still need the W7, but I am well aware of the security risks.

Thanks for all your help.

---

### Post by TheFu on 2022-08-12
Cloning copies everything, including UUIDs.
Having duplicate UUIDs in the same system is a problem.  Perhaps I missed where you removed the original drive?

---

### Post by mdiemer on 2022-08-12
Not sure I understand you, but here is what I now have permanently on the computer:

WD Black 1 TB HDD, the "C" drive. dual boot with Ubuntu and windows.

WD Black 1 TB HDD, the "D" drive. Music sample libraries for Windows.

Samsung M.2 PCIe 500 GB drive. Music sample libraries for Linux.

Additionally, a 3 TB WD Passport, for saving externally. I also have a 500 GB glyph drive connected, but that gets turned on  and off as needed (has its own off/on switch, so it doesn't show up unless turned on).
 
All the other drives were temporary, just used them to see if what I wanted to do was feasible. they are not in the computer anymore.

I plan to image the C drive, not clone to another disk, just have it on an external drive in case the C drive dies.

---

