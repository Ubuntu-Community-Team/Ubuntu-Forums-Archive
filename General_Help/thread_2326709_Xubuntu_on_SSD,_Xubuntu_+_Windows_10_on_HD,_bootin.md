---
title: "Xubuntu on SSD, Xubuntu + Windows 10 on HD, booting?"
date: 2016-06-03
forum: General Help
---

### Post by makem2 on 2016-06-03
Hi,

I have Xubuntu and Windows 10 dual-booting on my my laptop HD. I have just installed a 120GB SSD drive in the DVD bay using a caddy.

I want to install another Xubuntu on the SSD drive now, then, transfer all the current data and settings from the existing installation and then wipe that install from the HD when all is working.

I am wondering what will be the result as far as  the boot is concerned. Will grub provide the usual boot list with the default being the last install of Xubuntu?

Can you foresee any problems choosing partitions (/; home; swap)? I would hope that as the install is on a separate drive it will be obvious.

I would think the best way to start is to use a live USB and see what happens.

---

### Post by oldfred on 2016-06-03
Is system UEFI or BIOS?

Can you boot SSD from DVD bay. Some systems work and others do not and only boot from internal drive.

Do you have separate /home now? Do you want to keep it or copy most/all of it to SSD?

I do new clean install on SSD, and keep /home inside / (root), but all my data is in /mnt/data on HDD.

Either way, good backups are required. For both Windows & Ubuntu.

---

### Post by makem2 on 2016-06-03
Thanks for the quick reply.

System is UEFI

I don't know if I can boot from the DVD bay, assumed I would be able to so need to research.

I have a separate /home and would like to keep all of it.

I backup Xubuntu and Windows to a HD on a Raspeberry pi and then copy that backup to a second HD on the same Raspeberry pi.

I would have a separate /home and a separate data store on the HD which I only use if I really have to.

I have a live usb of xubuntu and set the laptop to boot from usb. It comes up with the usual choices and after choosing to check what I see first before actually installing, I am getting an error. It is quite long but relates to something timing out. I then get a welcome to Linux and am left in command mode at xubuntu@xubuntu~: or something similar

If I shut down and reboot, the usb is by-passed and the HD xubuntu starts up.

I will try to get the error message.

I am attempting to avoid opening up the laptop which is still in warranty although only just.

The actual error follows the splash screen and is:

[19.528674].hda_intel: azx_get_response timeout, switching to single cmd mode: last cmd=0x000f001

Welcome to Ubuntu etc

xubuntu@xubuntu:~$

The reason may be:

[http://askubuntu.com/questions/434814/ubuntu-will-load-but-not-xubuntu](http://askubuntu.com/questions/434814/ubuntu-will-load-but-not-xubuntu)

I had used 12.04

Well, after booting from a 14.04 version it jumped straight into a live session - no options at all.

In the live session the SSD drive was seen and could be written to. Not sure if this proves anything.

I am unable to find and answer to the question, "Can you boot from the SSD in the DVD bay?" and am not sure how to go about testing without the risk of messing up.

---

### Post by oldfred on 2016-06-03
If a new system, you may need the newest version of Ubuntu.
New hardware almost always needs some updates to software. And most vendors do not directly support Linux. So updates have to be made to kernel & various drivers, then those updates once approved and released will be added to a distribution. But few Linux distributions are rolling releases, so you have a time until next distribution is release.

Intel does provide some help. But some of the updates from Intel are fixing Skylake issues and even improving Haswell. The next generation will be out in a month or two.

My new Skylake build has worked fine with 16.04.

What brand, model, cpu, and video card is your system?

You may just have to install to SSD and see if it works. But if UEFI, grub will only install to the ESP on sda. So you will start booting from sda anyway. One or two users did end up having to put a /boot on the internal drive, but could have rest of system on removeable bay. 

If UEFI/gpt, be sure to partition SSD with gpt. And I like to include both the ESP - efi system partition and a bios_grub partition at the beginning of every drive. Then if you moved to internal drive, it could be configured to boot, without having to totally repartition.

---

### Post by makem2 on 2016-06-04
Satellite P50-C            
            Model: P50-C-12Z            
            Part No.: PSPTSE-01800REN            
            Serial No.:
            Warranty: 
            i7 2.4GHz 2401 Mhx 2 cores 4 logical processors            
            16GB memory             


```

makem@newTOSH:~$ sudo parted -l
[sudo] password for makem: 
Model: ATA TOSHIBA MQ02ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  1075MB  1074MB  ntfs            Basic data partition          hidden, diag
 2      1075MB  1180MB  105MB   fat32           EFI system partition          boot
 3      1180MB  1314MB  134MB                   Microsoft reserved partition  msftres
 4      1314MB  82.7GB  81.3GB  ntfs            Basic data partition          msftdata
 5      82.7GB  450GB   367GB   ntfs            Basic data partition          msftdata
 8      450GB   516GB   66.6GB  ext4
 9      516GB   980GB   464GB   ext4
10      980GB   986GB   6300MB  linux-swap(v1)
 6      986GB   987GB   500MB   ntfs                                          hidden, diag
 7      987GB   1000GB  13.2GB  ntfs            Basic data partition          hidden, diag




makem@newTOSH:~$ 

```

GPU:

[COLOR=#666666][FONT=arial] NVIDIA® GeForce® 930M with NVIDIA® Optimus&#8482; Technology [/FONT][/COLOR]
[COLOR=#666666][FONT=arial]memory amount : 2GB dedicated VRAM [/FONT][/COLOR]
[COLOR=#666666][FONT=arial]memory type : DDR3 Video RAM 
[/FONT][/COLOR][COLOR=#666666][FONT=arial]


[/FONT][/COLOR][COLOR=#000000]Your comment, "But if UEFI, grub will only install to the ESP on sda. So you will start booting from sda anyway. One or two users did end up having to put a /boot on the internal drive, but could have rest of system on removeable bay. " Concerns me as a new Linux user.

What are the implications of, "[/COLOR][COLOR=#000000]So you will start booting from sda anyway".

[/COLOR][COLOR=#000000]If I could end up booting from the Hdd then as far as I am concerned, it defeats the object of having an SSD. I dont need any speed when using the laptop and only received the SSD as a gift. It would be nice to have a quicker boot but thats all really. So, I am wondering if I should just use the SSD as storage and maybe some time later (a long time maybe), I swap the drives over.

[/COLOR]The installation I have now works perfectly and I dont want to risk messing it up but instead do a full re-install when I must for some reason.

I would value your opinion.

I now understand the meaning of ESP and from your comment it would seem that either way I will end up booting from the HD, /boot on the HD or not.

---

### Post by oldfred on 2016-06-04
It is just the boot loader part of grub that is in ESP - efi system partition.
The /EFI/ubuntu has a tiny 3 line grub.cfg that is a configfile to the rest of grub in your install.
It is more like the MBR and core.img that is in the sectors after the MBR with BIOS. But UEFI partition can have many boot loaders.

I find SSD very quick for booting. But I have at least one full install on every drive. 
If you just want to test it, just put a new install on SSD.

But be sure to backup ESP, as an install to sdb will overwrite the /EFI/ubuntu folder with the new install's UUID in the grub.cfg. The 3 line grub.cfg is about all that changes, so I have learned with my 2nd installs to have /EFI/ubuntu backed up. New versions make it a bit more difficult to work with ESP. Before it was mounted in fstab with defaults, but now they use 0077 which locks it. So I change back to defaults. If you run Boot-Repair that is also one of the first things it does.

---

### Post by makem2 on 2016-06-04
So, I gather you would give it a try in case it does boot from the SSD.

How do I back up the ESP? Is it the [COLOR=#000000] /EFI/ubuntu folder that needs to be copied and can it just be replaced if things go wrong?

I will read the [/COLOR][COLOR=#000080]UEFI boot install & repair link you give but this is beginning to look quite daunting.[/COLOR]

---

### Post by oldfred on 2016-06-04
I recommend backing up the entire ESP, it is not large.
And unlike BIOS/MBR installs you can just copy files back to a new ESP. Sometimes UEFI finds all of them automatically, others seem to need help to add NVRAM settings.
If you physically disconnect a drive UEFI NVRAM forgets its settings for that drive, and you normally have to re-add them.

I also on all ESP partitions create /EFI/Boot/bootx64.efi. That file is the filename both Windows Ubuntu use to boot external drives or installers, but actual files of course are different. But internal drives also can now boot that. Many have a UEFI: hard drive entry or one can be added as another boot option. I copy /EFI/ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi. This is just really another backup/alternative boot option.

---

### Post by makem2 on 2016-06-04
You have gone beyond my present capabilities with confidence so, I think best leave well alone for the time being. Use the gift for storage or maybe, if it is possible, learn how to install programs to the SSD instead of default as you can do in windows. That should show some speed difference for the program.

I thank you for the interest shown and the help in learning.

---

### Post by oldfred on 2016-06-04
At least now set up new SSD with gpt and include the ESP and maybe a bios_grub partition. 
I do that for all new drives, even larger flash drives, and even if currently planned as a data drive.

       t is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]

---

### Post by makem2 on 2016-06-04
I am sorry but I am totally lost here!
snip> "[COLOR=#000000]include the ESP and maybe a bios_grub partition" <snip
snip> "[/COLOR][COLOR=#000000]1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)" <snip Ctradicts above?[/COLOR]

[COLOR=#000000]Are you suggesting I set up the SSD partitions as if it were going to be a bootable drive and use the /home partition for data temporarily?

How do I include the ESP? Normally I just do the steps you mention above (1,2, 3)

I am sorry I may appear to be asking to be spoon fed but until I am perfectly confident I cant make changes. I think it is best to research the information you have given until I understand all.

Added to that I have just noticed the SSD drive has disappeared from the device list. After a BIOS update it has returned. I was told that an SSD would not work in a caddy in this machine. Toshiba said the mobo did not have the connectors and the recommended repairers said they would need to bend metal, add cables, charge £400 and it may not work.

All proved wrong but I hope it does not prove flaky.

GParted shows it is on /dev/sdb1 (with exclamation) system unknown, flags msftres and /dev/sdb2 ntfs /media/makem/120GB SSD flags msftdata

So it seems happy to be working happily.

Formatted /dev/sdb1 to fat32 size is 128MiB 1.99 MiB used

I hope that is right.

I believe I should now delete the NTFS partition after unmounting and create /, home and swap partitions as usual. I don't need Windows to access this drive.[/COLOR]

Drive info:

```
makem@newTOSH:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
udev            7.8G   12K  7.8G   1% /dev
tmpfs           1.6G  1.4M  1.6G   1% /run
/dev/sda8        61G   13G   46G  22% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            7.8G  7.1M  7.8G   1% /run/shm
none            100M   24K  100M   1% /run/user
tmpfs           1.0G   13M 1012M   2% /media/ramdisk
/dev/sda9       426G  157G  247G  39% /home
tmpfs           102M  2.9M  100M   3% /home/makem/.cache
/dev/sda2        96M   56M   41M  58% /boot/efi
/dev/sdb2       112G  108M  112G   1% /media/makem/120GB SSD
makem@newTOSH:~$
makem@newTOSH:~$ sudo fdisk -l
[sudo] password for makem: 


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5de19ff1


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   234441647   117220823+  ee  GPT
makem@newTOSH:~$ 




```

---

### Post by oldfred on 2016-06-04
You must have used Windows to gpt partition sdb.

Windows creates its system reserved 128MB unformatted partition before the first NTFS partition.
It functions somewhat like the bios_grub as unformatted space to stuff data. 
With BIOS Windows would write some data into the sectors after the MBR and grub would write data in the sectors after the MBR. And of course conflicts occurred.
But with gpt each has created new partitions to store that data it wants.

I just like to have both the ESP - efi system partition and a bios_grub at the beginning of every drive. Difficult to add when drive has lots of data & you decide to make it a boot drive. Neither ESP nor bios_grub are large, so no real space lost. 

If never installing Windows on sdb, you will not need the Windows system reserved partition.

---

### Post by makem2 on 2016-06-05
I received the drive as a gift from someone who used the drive in his sole Windows machine.

I am quite happy to wipe the whole drive and start from the beginning and will do that today. It will be interesting to see what happens as I have always had Windows on my own drives until adding Linux. I will find some guidance before starting though.

Looking at the partitions on my HDDI see that same 128MB partition which did not have a file system too.

Edit: It seems that when I shut down the machine (not sure about a reboot), that I lose the SSD drive. It returns if I boot into Windows and then back to Xubuntu, I see you mention conflicts so when the drives is back I will remove all partitions and attempt making it a solely Linux drive.If it does beome  boot drive later then Windows will boot from the HDD

After deleting the partitions Gparted no longer sees the drive after a reboot but windows does and after Windows, Gparted can again see the SSD.

At the moment I am wondering what would happen on a solely linux machine if I introduced a blank drive to the system. How would I be able to set partitions if it cannot be seen.

This is annoying and making me wonder if I can use the SSD at all in linux. I was warned that the BIOS may not see the drive in a caddy. (Toshiba didn't specify the OS though)

It is now formatted as one partition, ext4 and reappears after a reboot but not after a shut down. I need windows to get to be able to see the drive in linux!

Maybe I need to make a dual boot on the SSD either where it is or after using it to replace the HDD.

Edit: Just noticed that the SSD has disappeared while doing other things such as browsing and reading web pages.

---

### Post by oldfred on 2016-06-05
It is normal that Windows would not see drive.
And I think UEFI only can see for booting the MBR if booting in BIOS mode or the ESP if booting in UEFI mode.

But in drive list UEFI should always show all drives.

If formatted ext4, Windows will not see it as it does not know about Linux partitions. If you want to share data with Windows best to have a shared NTFS data partition, and not use Windows system partition as read/write from Linux.
And if newer Windows 8 or later you need Windows fast start up or always on hibernation off, for Linux to see any NTFS partitions. The hibernation leaves them mounted and the Linux NTFS driver will not mount them read/write if hibernated.

---

### Post by makem2 on 2016-06-05
Windows can always see the SSD even when formatted ext4 but of course it cannot read it. Linux can never see the drive after a reboot or even seems to lose it while running. Linux sees the existing  NTFS partitions on the HDD and windows sees but cannot the read ext4 partitions. Therefore all is ok on the HDD, it is just this SSD and I am not sure if it is BIOS causing the trouble. Why would a reboot after windows is shutdown allow linux to see the drive when before it could not see it? That is puzzling.

Using Gparted I now have the following partitions on the SSD:

[COLOR=#000000]300 MB efi FAT32 w/boot flag[/COLOR]
[COLOR=#000000]2 MB No Format w/bios_grub flag
111.49 GiB Format ext4 w/msftdata flag Label: Data

I have created a file /media/makem[/COLOR][COLOR=#000000]/UEFI/Boot/bootx64.efi

[/COLOR][COLOR=#000000]I have a new Device in the list: UEFI boot in which is a file boot64.efi

Following a boot fromlinux straight back to linux the SSD has again disappeared. Maybe I need to make it auto mount?

Answer = Yes, Data partition mounts ok after adding it to /etc/fstab

[/COLOR]

---

### Post by makem2 on 2016-06-05
Final temporary partitioning:

```

makem@newTOSH:~$ lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda       8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1    8:1    0     1G  0 part 
&#9500;&#9472;sda2    8:2    0   100M  0 part /boot/efi
&#9500;&#9472;sda3    8:3    0   128M  0 part 
&#9500;&#9472;sda4    8:4    0  75.8G  0 part 
&#9500;&#9472;sda5    8:5    0 341.8G  0 part 
&#9500;&#9472;sda6    8:6    0   477M  0 part 
&#9500;&#9472;sda7    8:7    0  12.3G  0 part 
&#9500;&#9472;sda8    8:8    0    62G  0 part /
&#9500;&#9472;sda9    8:9    0 432.1G  0 part /home
&#9492;&#9472;sda10   8:10   0   5.9G  0 part [SWAP]
sdb       8:16   0 111.8G  0 disk 
&#9500;&#9472;sdb1    8:17   0   300M  0 part 
&#9500;&#9472;sdb2    8:18   0     2M  0 part 
&#9500;&#9472;sdb3    8:19   0    30G  0 part /home/makem/linux2
&#9500;&#9472;sdb4    8:20   0  79.5G  0 part /home/makem/data
&#9492;&#9472;sdb5    8:21   0     2G  0 part 
makem@newTOSH:~$ 

```

Many thanks oldfred :D

---

### Post by makem2 on 2016-06-07
[COLOR=#000000]Thank you all for your input.[/COLOR]

[COLOR=#000000]The SSD is not compatible with Intel chip set 8 or greater. My chipset is greater.[/COLOR]

[COLOR=#000000]Reason why it works in Windows - windows does not need special drivers.[/COLOR]

[COLOR=#000000]It 'may' work as a main drive.[/COLOR]

[COLOR=#000000]This information comes from OCZ the suppliers of the SSD. As a matter of interest that are part of Toshiba, have online chat and great quick support.[/COLOR]

[COLOR=#000000]Having had the SSD as a gift I have lost nothing but have gained much knowledge and also got the bug for SSD[/COLOR]

[COLOR=#000000]I am considering the OCZ-Vector-180-SSD-VTR180-25SAT3-240G-2-5-SATA-6Gb-240GB-SSD.[/COLOR]

[COLOR=#000000]They supply free cloning software (one of the worries I had) and a 5 year guarantee.[/COLOR]

[COLOR=#000000]I will dispose of the SSD somehow and have the new SSD as main drive and the current HDD in the caddy.[/COLOR]

---

