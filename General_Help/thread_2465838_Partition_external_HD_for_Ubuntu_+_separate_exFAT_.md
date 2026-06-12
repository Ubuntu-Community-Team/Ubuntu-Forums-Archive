---
title: "Partition external HD for Ubuntu + separate exFAT partition"
date: 2021-08-12
forum: General Help
---

### Post by wallsfour on 2021-08-12
I'm new to Linux/Ubuntu (I'm from macOS). I've researched how to install Ubuntu on an external HD (as well as file systems, Linux in general) for most of the day. I understand the initial steps: 1. Have Ubuntu bootable from USB flash drive, created using Etcher, and 2. Boot up the USB flash drive, install Ubuntu on external HD (check "install drivers" box, choose "Something else," etc.).

However, there is one step which I'm not certain, which is partitioning the external HD, because:

[LIST]
[*]I'm confused about the "RAM partition" and "SWAP partition" (or any other required partition)—especially since the tutorials I've found each do things differently and/or don't explain much.
[*]My set-up is also a bit more specific, since I'm on macOS, and of the 1TB, I want to have 300GB for Ubuntu, and 700GB partitioned as exFAT for file storage (macOS can read, but not write on NTFS)—would I need to make this partition on macOS beforehand?
[/LIST]
**Could anyone please direct me on how to partition an external drive for Ubuntu (RAM partition/SWAP partition if needed, 300GB for Ubuntu)—with also a 700GB exFAT partition as file storage?**

---

### Post by TheFu on 2021-08-12
Wipe the external drive.

Linux must be installed onto Linux-native file systems, just like OSX. It cannot be run of exFAT or NTFS.

There's no "RAM" partition.

If you are really new, accept the defaults, just be certain NOT to write to any storage you don't want wiped.  If you aren't 100% certain, unplug the other storage devices in the system for the installation.

Everyone has a different opinion about disk layouts, which means there are lots and lots of different needs and everyone has their own experiences which lead them to their answer.

BTW, 300G in a single partition for Linux isn't ever what I'd recommend for a number of reasons.
[Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) has a layout with reasons for "why".  The only change today would be for / to be 35G - Ubuntu has become much more bloated since 2019.

For an SSD or HDD, there is little reason to use exFAT. Use NTFS if you want cross-platform access to a data partition and plan to physically connect it.  For over the network access, stay with EXT4 as the file system or if it is a flash drive, a case could be made to use f2fs instead - definitely not exFAT.

As for how, use gparted. Best to start by laying down a fresh GPT, then creating the new partitions as needed.  I don't think OSX can make Linux partitions+file systems.  Boot into a "Try Ubuntu" setup and do that.  The Ubuntu installation disk should have a "Try Ubuntu" environment which will work.  Keep that around as a backup for the next year. A few things are easily fixed from that environment and in a multi-boot environment, each OS is likely to screw over the others on the same machine (cough - MSFT).

If you are really new, I'd actually prefer it if you didn't do a multi-boot setup at all. Start by using a virtual machine and become comfortable with Linux that way for 6-12 months first. There is almost zero risk to your OS and VMs run very fast these days provided you don't expect high-end games to be fast.  For non-GPU program, 90-95% of native performance is easily possible inside a VM.

---

### Post by tea for one on 2021-08-12
Are you familiar with UEFI and Legacy boot modes.

Have a look at this before installing [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also, you need to be aware that an OS installation to an external device can create boot problems when the external drive is not connected.

Do you know if you can you remove, isolate or de-activate your internal drive?

---

### Post by oldfred on 2021-08-12
Note that Ubuntu's Ubiquity installer in UEFI mode only installs grub bootloader into first drive. Usually then your internal drive. It then does not create an ESP - efi system partition on external drive, nor use it if it exists. Ubiauitu installer creates an "ubuntu" entry like an internal drive and that works if external drive always connected. But external drives boot from the ESP using /EFI/Boot/bootx64.efi, just like the installer uses. That choice must be made in UEFI boot menu each time.


At minimum, partition in advance & include an ESP  on external drive.
Only use Something Else install process. If partitioned in advance with gparted, you choose (change button) which partition you want for / (root) & /home if separate partition. If using swap partition it auto finds that.

You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

Several work arounds. 
Remove internal drive, so only drive seen by installer is external drive.
Temporarily remove esp,boot flags from internal drive, so ESP on external is only ESP seen by installer.
In middle of install process, unmount internal drive's ESP & mount external drive's ESP.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I would make ESP as first partition of about 300 to 500MB. And swap as last partition (right as seen in gparted). So then you can more easily adjust partitions in middle. I typically do not fully allocate drive initially so I have some room for another data partition or test install or expanding an existing partition.

---

### Post by wallsfour on 2021-08-13
> **tea for one said:**
> Are you familiar with UEFI and Legacy boot modes. Have a look at this before installing [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Thanks for the link, however, I'm on a Mac. My Ubuntu setup would be on an external 1TB USB 3.0 HDD (7200RPM).

---

### Post by wallsfour on 2021-08-13
> **TheFu said:**
> If you are really new, accept the defaults, just be certain NOT to write to any storage you don't want wiped. If you aren't 100% certain, unplug the other storage devices in the system for the installation.
External HDD is 1TB and internal drive is 256GB, so should be easily distinguishable (more worried about opening my laptop and accidentally breaking something).
> **TheFu said:**
> For an SSD or HDD, there is little reason to use exFAT. Use NTFS if you want cross-platform access to a data partition and plan to physically connect it. For over the network access, stay with EXT4 as the file system or if it is a flash drive, a case could be made to use f2fs instead - definitely not exFAT.
[...]
As for how, use gparted.
Basically, what I want to do is, on a 1TB 7200RPM external HDD, I want to have a partition for Ubuntu, and another partition for storage of random files (accessed using macOS). Since macOS can read but not write on NTFS, the second partition would need to be APFS (Apple) or exFAT.

*However*, I believe that having two partitions on the external HDD, and also with different file systems, is starting to sound like a bad idea (don't even know if I would be able to boot Ubuntu).

---

### Post by wallsfour on 2021-08-13
> **oldfred said:**
> [...]
Thanks for the reply, but it's way too advanced for me (just started with Linux this week). I'll try to come back and re-read the post when I know more about Linux.

---

### Post by oldfred on 2021-08-13
If you do not create an ESP on the external drive, it will only be bootable from the system you install it from.
As long as you have an ESP on it and use gpt partitioning, then you can repair it afterwards. 
You can use gparted which is on Ubuntu live installer, or gparted also has its own live ISO.

Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[https://gparted.org/news.php](https://gparted.org/news.php)
GParted partitioning software - Full tutorial Older, but gparted has not really changed. But it still defaults to old MBR partitioning.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting adding partitions.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by wallsfour on 2021-08-13
[COLOR=#000000][FONT=Helvetica]Today I researched more about the partitioning step that I had difficulty with.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Since my external HDD is 7200RPM, I would like to have a SWAP partition. I would also like to have a /home partition. 

I found [this]("https://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/") tutorial which seems helpful for allocating partitions—and following it, my 1TB external HDD would look something like this:[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]- 20 GB root[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]- 16 GB swap (have 8GB of RAM)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]- 400 GB /home[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]- 564 GB unused (according to tutorial: "Most distributions of Linux use either ext3 or ext4 as their file system nowadays, which has a built-in 'self-cleaning' mechanism so you don’t have to defrag. In order for this to work best, though, there should be free space for between 25-35% of the partition."[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Is this good?[/FONT][/COLOR]

---

### Post by wallsfour on 2021-08-13
> **oldfred said:**
> If you do not create an ESP on the external drive, it will only be bootable from the system you install it from.
As long as you have an ESP on it and use gpt partitioning, then you can repair it afterwards. 
You can use gparted which is on Ubuntu live installer, or gparted also has its own live ISO.

Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[https://gparted.org/news.php](https://gparted.org/news.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Okay, thanks, I'll look into that. 

However, if it's relevant, I would partitioning and installing Ubuntu with a bootable USB flash drive, with the ISO file of Ubuntu installed on it using balenaEthcher (similar software to Rufus).

---

### Post by oldfred on 2021-08-13
I would first add ESP, and make / larger like 35 to 50GB. I am actually using 12GB in my 30GB /, but it is growing even though I houseclean regularly.And snaps (which I do not use) take a lot more space.

I would only make swap as 4+, GB. Unless you hibernate you do not need large swap when you have as much RAM as you have.
And with Linux you can boot in almost the same time as restore from hibernate and avoid all the hibernated issues.
The old 2x size for swap was way back when RAM was in MB, not GB. Then swap was used a bit more. With my older 4G system, I never used swap, but 1.5GB system used swap if I loaded too many larger apps. So learned not to have too many tabs in Browser or too many large apps open at once.

---

### Post by TheFu on 2021-08-13
> **wallsfour said:**
> 
- 20 GB root
- 16 GB swap (have 8GB of RAM)
- 400 GB /home
- 564 GB unused (according to tutorial: "Most distributions of Linux use either ext3 or ext4 as their file system nowadays, which has a built-in 'self-cleaning' mechanism so you don&#8217;t have to defrag. In order for this to work best, though, there should be free space for between 25-35% of the partition."

Is this good?

Wow, there was a bunch of font and colors in that post. No need for that here.
Here's what I would do on a 20.04 or later system:

[LIST]
[*] 35 GB root
[*] 40 GB /home
[*] 4.1 GB swap
[*] {whatever is left} GB unused
[/LIST]

If you use LVM, then resizing larger on a running system is 5 seconds.  You would have logical volumes for swap, home, root.  
If you don't use LVM, then leaving some slack space between each partition makes sense. You want to be able to increase the available space in an emergency, but not waste too much space. In that layout (partitions only, no LVM), I'd do something like this:
[LIST]
[*]0 - 2048b - empty (needed for partition alignment. Very important for performance)
[*]2048b - 50MB - /boot/efi
[*]50MB - 550MB - /boot
[*]551MB - 4.1GB - swap
[*]4.1G - 6G - empty/unallocated
[*]6G - 41G - root partition
[*]41G - 51G empty/unallocated
[*]51G - 91G /home
[*]92G - end ... empty/unallocated
[/LIST]
I hope that is clear about the empty areas between each partition.  Also, be certain to use GPT, not MSDOS partitioning regardless.

With that layout, you can quickly add a little more storage for swap or the root partition or /home as needed, but without being trapped.
We wasted just 16G of space for all this flexibility. Don't get hung up on the exact locations for the split. A little bigger or a little smaller is close enough, just be 100% certain that every partition starts on a 4Kb boundary. Gparted/parted should force that, unless you enter too specific size information. Stay with 1MB /1GB size chunks and it should be fine.

If you want a place for pure data, do that allocation from the end backwards, just know that going left is much harder than going right in the partitioning world.  With LVM, the location of LVs isn't something that matters and we can add more storage to any LV as needed - the volume manager deals with it, provided it is all in the same VG.

Also, we can remove the swap partition, delete it and recreate a new one anywhere there is free storage without too much trouble or risk, so that 4.1 as swap is more slack, should it be needed. I doubt it will, however.

I think /boot still needs to be outside LVM - 500MB should be plenty and the EFI partition (FAT32 is mandated) at 50MB based on these actual numbers:
```
Filesystem                            Type  Size  Used Avail Use% Mounted on
/dev/sda2                             ext2  721M  255M  430M  38% /boot
/dev/sda1                             vfat  511M  6.7M  505M   2% /boot/efi

```
/boot on that system has 3 kernels today.
/boot/efi is where different OSes place their EFI boot stuff. My example above is for 1 Ubuntu system only.  Looking through all my other systems, none use EFI, so that's my only data point.

I've been working on a script to do my initial partitions and LVM setup, but haven't tested it sufficiently for others to use. The GUI stuff for all these details gets ugly, when a script can make it so in 2 seconds.  Hummmm. I really need to test it more.

---

### Post by TheFu on 2021-08-13
Linux doesn't need defragging. That is true. 20-30% free?  That's just crazy talk.  If you leave 10G free, that should be fine or 3x the largest files you deal with.  If you deal with 40G files, then having 120G free makes sense.  If you deal with 15G files, 30-45G free makes sense.  On a 1TB disk, that isn't much space at all.

If SSD storage is used, the rules are very different. SSD storage is all virtual and the OS doesn't actually know which cells are used for writes. The SSD controller handles all the write balancing for us and can use over-provisioned storage when needed. To extend the life of an SSD, perhaps 20% unused will let the SSD controller have sufficient working space to do some amazing write level tricks.

---

### Post by oldfred on 2021-08-13
Did you mention what Mac?
Very old Mac used a 32 bit UEFI. Those were with core2 duo chips.
Very new Mac and now M1 Macs have various issues.
And it seems every generation of a Mac has some slightly different issue.
And video may be one of the issues, requiring video drivers or boot pameters.

Many with Mac use rEFInd boot loader. 
I use that as an emergency boot flash drive for my PC based UEFI system. It fits on an old tiny USB flash drive that I had retired as too small for anything.
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by TheFu on 2021-08-13
Mac?  Way to bury the lead!!!   Whenever posting setup questions anywhere, please, please, please, lead with that information.  Macs need special stuff, always. They make great Linux systems, especially if you wipe that other OS off. Lots of friends who have dumped OSX and moved to Linux.

If you are afraid of screwing things up - use a virtual machine setup.  That removes 99.999% chances that you might screw something up to impact the existing OS.  Whenever we do installFests at the local University, we push for them to install into virtual machines, not as dual boot.

---

### Post by wallsfour on 2021-08-14
> **TheFu said:**
> Mac?  Way to bury the lead!!!   Whenever posting setup questions anywhere, please, please, please, lead with that information.
1st sentence of the initial post: [I]I'm new to Linux/Ubuntu (I'm from macOS).

[/I]2nd post: [I]Thanks for the link, however, I'm on a Mac.

[/I]Also, 3rd post "macOS" mentioned twice.

You need new glasses. : ) : ) : )

---

### Post by wallsfour on 2021-08-14
> **oldfred said:**
> Did you mention what Mac?
2015 MacBook Pro laptop, 8GB of RAM with 256GB SSD.

However..., I'll be installing Ubuntu on an external 1TB USB 3.0 7200RPM HDD&#8212;installed using a booted Ubuntu ISO file on a USB flash drive.

---

### Post by wallsfour on 2021-08-14
> **TheFu said:**
> Here's what I would do on a 20.04 or later system:

[LIST]
[*] 35 GB root
[*] 40 GB /home
[*] 4.1 GB swap
[*] {whatever is left} GB unused
[/LIST]

If you use LVM, then resizing larger on a running system is 5 seconds.  You would have logical volumes for swap, home, root.
If I use LVM, can I increase the 40GB /home to something higher in the future?
> **TheFu said:**
> Linux doesn't need defragging. That is true. 20-30% free? That's just crazy talk. If you leave 10G free, that should be fine or 3x the largest files you deal with.
Thanks, will leave a smaller % of unused space.
> **TheFu said:**
> Also, be certain to use GPT, not MSDOS partitioning regardless.
So using GParted, when installing Ubuntu on the 1TB external HDD (from the bootable ISO file on a USB flash drive), I set the partition tables of the root, home and swap as GPT, not MSDOS?

---

### Post by oldfred on 2021-08-14
You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

Unless drive already gpt, drive is over 2TiB or you are installing in UEFI mode, the installer defaults to MBR. And Ubuntu will install in UEFI mode to MBR drive, even though it really should not.

Also gparted defaults to MBR, so you have to make sure to change to gpt first, before starting partitioning. Gpt partitioning is the default for a Mac, so if you use its tools the drive should be gpt.

Another install to a second drive. While not Mac otherwise similar.
[https://ubuntuforums.org/showthread.php?t=2465696](https://ubuntuforums.org/showthread.php?t=2465696)

---

### Post by yancek on 2021-08-14
> If I use LVM, can I increase the 40GB /home to something higher in the future?
 	 		 			 			 				 					  

Yes you can.  You can also do this with a standard install when NOT using LVM.  You generally need free or unallocated space continguous to the partition you want to increase in size.

Linux filesystems generally need 5-10% of the partition free so when your partition gets to be 90%, you will problems using it.  You can check this by running the df -h command which will tell you the amount of space used on any partition thaat is mounted.

Current Ubuntu installs create a 4GB swap file rather than a swap partition.  With 8GB of RAM, you probably won't need more swap unless you are hibernating as pointed out above.

>   			 		 	 So using GParted, when installing Ubuntu on the 1TB external HDD  (from the bootable ISO file on a USB flash drive), I set the partition  tables of the root, home and swap as GPT, not MSDOS? 		 

No.  You set the hard drive as GPT  Before installing Ubuntu from your usb, open gparted which is on the Ubuntu usb.  Type:  sudo gparted and the gparted window should open.  Look in the upper right of the gparted window and click the down arrow to make sure you have the correct drive.  This should be easy as it shows the type of drive and the size.  When you have done that and verified you have the correct drive showing, click on the Device tab and you will see the option to Create Partition table .  After doing that, you will get the msdo or gpt optoin.

I would suggest you keep the Ubuntu install media as it can be used if you have problems later and also because it has gparted on it.

The link below is to the GParted Manual.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by TheFu on 2021-08-14
Seems the forum software doesn't like my answer/excuse for the Mac stuff.  [https://paste.ubuntu.com/p/9Yf9Xd6tYs/](https://paste.ubuntu.com/p/9Yf9Xd6tYs/) has the text. Expires in a month. Not too important, but hopefully a moderator will get this to the team working on all the forum post bugs and it can be solved.

---

### Post by Dennis N on 2021-08-14
> If I use LVM, can I increase the 40GB /home to something higher in the future? 
If you plan to use LVM, read up on it first so that you understand what it is. It also requires special terminal commands to manage. In particular, to have root and home of a user-specified size in you system, you need to set up these LVM structures before using the installer. But the rewards far outweigh the initial learning curve. Personally, I would never go back to standard installs using whole partitions*.

* exception: when creating a virtual machine.

---

### Post by TheFu on 2021-08-14
> **wallsfour said:**
> If I use LVM, can I increase the 40GB /home to something higher in the future?
Yes. 5 seconds, while the system keeps running.  **sudo lvextend -r -L +5G /dev/{vgname}/{lvname}** will take 5G from the available VG storage and allocate it to the LV, and extend the file system to use that new space.  The file system needs to be ext4 for this to work. No screwing with the fstab. No running other commands. Add the storage when it is needed, where it is needed.  No reboot needed.  That's the real power of LVM.

In almost 30 yrs as a Unix Admin, I've never been able to perfectly guess how much storage is needed, where, on any system.  With LVM, I don't need to. I allocate for 3 months at a time.  When space gets tight, I get a message about it, and check how much is available in the VG, then allocate what I feel should last the next 3 months.  If there isn't any more free space in the VG, I have about 3 months warning to get more storage or start pruning junk.

You can also add other logical volumes for other needs.  Most of the time, an LV can be considered an extremely flexible partition that can be easily increased in size later, provided the VG has available storage.  

Plus, with LVM, you have access to snapshots at the volume management layer.  The power in this capability is fantastic.  Lots of people don't use snapshots, which is fine. The easy resizing of LVs is still worth it.  With snapshots, we can freeze blocks of storage (instantaneously) and mount those snapshots for other needs - like getting a perfect backup while the system keeps running.  Or just do a snapshot before your weekly patching, so if anything bad happens, you can fall back to the snapshot point quickly like the failed update never happened.  Snapshots don't replace backups, but they are part of the enterprise tools that LVM provides.  

There are lots of other things LVM can do.  If you want to move to a new HDD, moving the entire PV from 1 disk to another is 1 command and it can be used ON A RUNNING SYSTEM!  
Or suppose you want to convert from a single SSD into a RAID1 setup for safety?  Adding another drive and making it a RAID1 (mirror) isn't hard.  Or suppose you want to break a RAID1 into 2 separate devices?  Easy. Thanks to LVM.  Almost all LVM commands work while the system keeps running.

Ever wonder how Google can provide 100G of free storage to everyone?  They don't, not really.  They use something called "thin provisioning" which is another LVM capability.  All the users see they have 100G, but that is taken from a pool of storage that is oversubscribed.  They might have a 10TB disk which would support 100 users, but they might put the data for 500 or 1000 users onto that *thin provisioned* storage. As long as everyone doesn't use the upper limit of space, then it will probably be fine. Plus, uploading 100G takes time, so Google can move the heavy users to different storage before the TP amount is used completely.  All thanks to LVM.  The same works for all those VPS - virtual private servers - that provide 20G of storage. There really isn't 20G available to everyone, but it reports that there is.  Most of my Linux servers use 5-10G, so with thin provisioning the host can make more efficient use of the 20G they sell me, when I only need 5-10G.  It is human nature.

> **wallsfour said:**
> Thanks, will leave a smaller % of unused space.

Don't forget that file systems reserve storage to prevent out-of-storage problems for the root user. I think they reserve 5% by default - so 5% of 1TB isn't a tiny amount.  Only root privileged processes can use that last 5% of storage, not end users.  On the application and OS LVs/partitions, that 5% is a good idea, but on 100% data-only storage, it is a complete waste of storage that can be used.  On a 4TB disk, 5% is 200GB! I don't know about you, but that seems wasteful.  We can tune that down or completely remove the reserved storage ... or use it as a last resort, emergency storage when everything gets full.

> **wallsfour said:**
> So using GParted, when installing Ubuntu on the 1TB external HDD (from the bootable ISO file on a USB flash drive), I set the partition tables of the root, home and swap as GPT, not MSDOS?

Well, if you use LVM, then root, home, and swap would be LVs all inside the same partition. That single partition would be marked as an LVM member.

But since you are on a Mac, I don't want to assume too much for what is truly needed.

Here are the partitions on an EFI-boot system that I setup yesterday with LVM as a test:
```
$ sudo parted -l /dev/vda
Model: Virtio Block Device (virtblk)
Disk /dev/vda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: **gpt**
Disk Flags: 

Number  Start   End     Size    File system  Name    Flags
 1      1049kB  2097kB  1049kB               GRUB    bios_grub
 2      2097kB  54.5MB  52.4MB  fat32        EFI-SP  **boot, esp**
 3      54.5MB  684MB   629MB   ext4         /boot
 4      684MB   21.5GB  20.8GB               LVM     **lvm**

$ df -Th
Filesystem            Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root ext4  9.8G  3.8G  5.5G  41% /
/dev/mapper/vg00-home ext4  5.2G   22M  4.9G   1% /home
/dev/vda3             ext4  575M  106M  428M  20% /boot
/dev/vda2             vfat   50M  5.2M   45M  11% /boot/efi
```

The LVM information:
```
$ sudo pvs
  PV         VG   Fmt  Attr PSize   PFree
  /dev/vda4  vg00 lvm2 a--  <19.36g 8.00m

$ sudo vgs
  VG   #PV #LV #SN Attr   VSize   VFree
  vg00   1   3   0 wz--n- <19.36g 8.00m

$ sudo lvs
  LV   VG   Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home vg00 -wi-ao----  5.25g                                                    
  root vg00 -wi-ao---- 10.00g                                                    
  swap vg00 -wi-ao----  4.10g      

$ lsblkt
NAME           SIZE TYPE FSTYPE      MOUNTPOINT
vda             20G disk             
&#9500;&#9472;vda1           1M part             
&#9500;&#9472;vda2          50M part vfat        /boot/efi
&#9500;&#9472;vda3         600M part ext4        /boot
&#9492;&#9472;vda4        19.4G part LVM2_member 
  &#9500;&#9472;vg00-swap  4.1G lvm  swap        [SWAP]
  &#9500;&#9472;vg00-root   10G lvm  ext4        /
  &#9492;&#9472;vg00-home  5.3G lvm  ext4        /home

```

Don't worry about the sizes for the LVs. I didn't have enough room to make *root* and *home* LVs full sized. Plus, this system will be deleted in the next few days. My goal was to get the partition types correctly setup to support both BIOS booting and UEFI booting, while getting a GPT partition table and using LVM with the base LVs that I'd like.  On a server, having a separate /home probably isn't needed, but on a desktop, it is extremely important, IMHO.

Setting up LVM requires picking the "do something else" option. During the installation process, I move to a different terminal and run a script to setup the partitions and LVM stuff, then switch back to the installer and assign the specific partitions and LVs do mount points. My script needs a better configuration method and some validation still. OTOH, I can't believe I waited this long to create it.

---

### Post by wallsfour on 2021-08-14
> **TheFu said:**
> Seems the forum software doesn't like my answer/excuse for the Mac stuff.  [https://paste.ubuntu.com/p/9Yf9Xd6tYs/](https://paste.ubuntu.com/p/9Yf9Xd6tYs/) has the text.
Happens even to the best of us. : ) I could have been clearer as well in the OP, though.

For macOS, it was initially "Mac OS X," and then only "OS X" ("X" as the Roman numeral, for tenth version). Especially for "Big Sur," which is version 11, Apple changed the naming to "macOS"&#8212;however, they made the switch in advance in 2016, while still having 10.X versions. Just learned about this by searching it, and I'm actually on a Mac, so I don't blame you at all for not knowing this. : ) (Might want to switch from "OS X" to "macOS" though, since that was changed around 5 years ago, and OS X versions aren't supported anymore. : ) )

If you want a reference list, the macOS version history Wiki page and table are good: [https://en.wikipedia.org/wiki/MacOS_version_history#Releases](https://en.wikipedia.org/wiki/MacOS_version_history#Releases)
> OSX doesn't write NTFS? Ouch. A quick search finds that ntfs-3g is available for OSX. That's the same code used in Linux.Good to know, that might come in handy.

---

### Post by wallsfour on 2021-08-14
> **Dennis N said:**
> If you plan to use LVM, read up on it first so that you understand what it is. It also requires special terminal commands to manage. In particular, to have root and home of a user-specified size in you system, you need to set up these LVM structures before using the installer. But the rewards far outweigh the initial learning curve. Personally, I would never go back to standard installs using whole partitions*.

* exception: when creating a virtual machine.
I'm interested in looking into it and learning it eventually, but using LVM isn't a requirement? If I do an installation of Ubuntu on an external HDD, using the booted ISO file on a USB flash drive, can I do it without knowing how to use LVM?

---

### Post by Dennis N on 2021-08-14
> **wallsfour said:**
> I'm interested in looking into it and learning it eventually, but using LVM isn't a requirement? If I do an installation of Ubuntu on an external HDD, using the booted ISO file on a USB flash drive, can I do it without knowing how to use LVM?
You don't need to use LVM. I did regular installs for years before doing one using LVM.

---

### Post by TheFu on 2021-08-14
> **wallsfour said:**
> I'm interested in looking into it and learning it eventually, but using LVM isn't a requirement? If I do an installation of Ubuntu on an external HDD, using the booted ISO file on a USB flash drive, can I do it without knowing how to use LVM?

LVM is definitely NOT a requirement.  The problem is that if you don't choose it at installation time, then only a fresh install will allow using it for the OS.  LVM is optional, and having the install setup the default LVM 100% automatically on the external device is possible. It just won't have the LVs sized very nicely (the / LV will be much, much, much, tool large and make backups and other things less great.

BTW, LVM doesn't have any GUI tools for management. It is 100% CLI.

One last time, I'd really recommend that you use a virtual machine to install Linux while you are learning. It removes nearly 100% of the risks to the existing system. Dual booting is a dangerous thing.

---

### Post by wallsfour on 2021-08-14
Okay, so I researched about the things mentioned:

**UEFI and BIOS**
I think Macs are UEFI by default? Nothing specific to do?
> Since 2006, _Mac computers with an Intel-based CPU use an Intel firmware based on the Extensible Firmware Interface (EFI) Development Kit (EDK) version 1 or version 2. EDK2-based code conforms to the Unified Extensible Firmware Interface (UEFI) specification_. This section refers to the Intel firmware as the UEFI firmware. The UEFI firmware was the first code to execute on the Intel chip.
Source: [https://support.apple.com/en-au/guide/security/seced055bcf6/web](https://support.apple.com/en-au/guide/security/seced055bcf6/web)

[B]EFI System Partition / ESP
[/B]I think I'm good for this. I should be fine plugging the external HDD, pressing the Option key when booting (if I don't press it, it will simply boot macOS), and then select the external HDD with Ubuntu installed on it.
> On macOS computers based on the x64 hardware architecture, the EFI system partition is initially left blank and unused for booting.[11] However, the EFI system partition is used as a staging area for firmware updates.[12] The logic usually goes as follows: the EFI first looks for a bootloader in ESP, and if there is none it will continue to the MacOS file system.
Source: [https://en.wikipedia.org/wiki/EFI_system_partition#macOS](https://en.wikipedia.org/wiki/EFI_system_partition#macOS)

**LVM**
If not required, I think I'll put that off for a later time.

**GPT and MSDOS/MBR partition table**
GPT seems to be the better option!


I think I should be ready to go, and install Ubuntu (on my external HDD). : )

---

### Post by Dennis N on 2021-08-14
Here are a couple of articles that offer some introduction:
[LVM Demistified]("http://www.linuxjournal.com/content/lvm-demystified")
[Ubuntu LVM Guide Part 1]("http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html")

> LVM doesn't have any GUI tools for management.
Not in Ubuntu, at least. There is a gui tool called blivet-gui but only Fedora seems to have it.

---

### Post by TheFu on 2021-08-14
If you let the Ubuntu installer deal with the partitioning, it should create the number and types of partitions minimally needed. If you don't choose LVM (or encryption), then it won't be used.  In ubuntu, the default  LUKs encryption setup uses LVM too.

Don't confuse EFI and UEFI. I think they are the same.

GPT **is** better for many reasons. I don't know of any downside to using it on hardware that is less than 10 yrs old.

---

### Post by wallsfour on 2021-08-14
> **TheFu said:**
> LVM is definitely NOT a requirement.  The problem is that if you don't choose it at installation time, then only a fresh install will allow using it for the OS.  LVM is optional, and having the install setup the default LVM 100% automatically on the external device is possible. It just won't have the LVs sized very nicely (the / LV will be much, much, much, tool large and make backups and other things less great.

BTW, LVM doesn't have any GUI tools for management. It is 100% CLI.
Okay, I think I want it (and better to do so). :P

> **TheFu said:**
> One last time, I'd really recommend that you use a virtual machine to install Linux while you are learning. It removes nearly 100% of the risks to the existing system. Dual booting is a dangerous thing.
I tried it. Actually, I have Ubuntu in VirtualBox/VM right now. However, when I create a partition table, it says it will "ERASE ALL DATA." 

I'm guessing this won't affect my Mac HD itself, but I realllllly don't want to risk it. Doing it on the external HDD itself, I wouldn't mind messing up, since I can simply re-format the external HDD if something happens.

---

### Post by Dennis N on 2021-08-14
> However, when I create a partition table, it says it will "ERASE ALL DATA."
The warning applies only to the drive selected in gparted's selection box at right-end of the gparted toolbar.

---

### Post by TheFu on 2021-08-14
> **wallsfour said:**
>  I tried it. Actually, I have Ubuntu in VirtualBox/VM right now. However, when I create a partition table, it says it will "ERASE ALL DATA." 

I'm guessing this won't affect my Mac HD itself, but I realllllly don't want to risk it. Doing it on the external HDD itself, I wouldn't mind messing up, since I can simply re-format the external HDD if something happens.

Yes, that is only for the virtual machine HDD - the .vdi file you created when setting up the VM virtual-hardware. If you put the VDI file on the external storage, probably just start with 100G at most.  VDI files can grow too. On HDDs, performance of the storage will make a huge difference to the performance of the VM.  Just know that with a spinning HDD, not using a sparse VDI setup will drastically improve performance.  Also know that with LVM, you can add additional VDI files and merge them into the same VG which means you can increase the size of the LVs beyond what any single VDI file size might be.  If the VDI files are on the same physical disk, there is little extra risk in doing this.  

**But if you let LVM VGs cross physical storage devices, the risks become much greater and total data loss is possible should 1 of those HDDs have a failure.  ** That's a very important warning.

The ubuntu installer won't go out of the VDI storage accidentally, ever, without you setting up a host-to-VM storage mount. And if you do that, the permissions will be different and some other things need to happen. There are multiple ways to do it. They are multi-step. No chance to accidentally do it.

---

### Post by wallsfour on 2021-08-15
Got everything to work! Installed Ubuntu on a my external HDD. Posting this right now from Ubuntu itself. : )
Was a bit stressed when doing partitions/formatting, but just logged back into macOS, and everything is still there. 

Thanks everyone for the help! I'm now officially a Linux user. : )

---

