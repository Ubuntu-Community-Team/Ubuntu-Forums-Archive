---
title: "NVME Grub Config help"
date: 2019-03-29
forum: General Help
---

### Post by Calandric on 2019-03-29
--EDIT--

Solved, see post# 34 for solution.  [https://ubuntuforums.org/showthread.php?t=2415658&page=4&p=13849399#post13849399](https://ubuntuforums.org/showthread.php?t=2415658&page=4&p=13849399#post13849399)


--ORIGINAL---------------------------------

Ok, so a brief background catch up.  I know my way around Linux a decent amount, but am by no means an expert.  My current PC specs are as follows:

```
[B][COLOR=#434343][FONT=Arial]ASUS P6X58D Premium LGA 1366 Intel X58 Motherboard
[/FONT][/COLOR][/B][B][COLOR=#434343][FONT=Arial]Intel Core i7-950 Bloomfield Quad-Core 3.06 GHz Processor
[/FONT][/COLOR][/B][B][COLOR=#434343][FONT=Arial]G.SKILL Ripjaws Series 12GB (3 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) RAM
[/FONT][/COLOR][/B][B][COLOR=#434343][FONT=Arial]EVGA GTX 1070 Hybrid Video Card
[/FONT][/COLOR][/B][B][COLOR=#434343][FONT=Arial]CORSAIR Hydro H70 CWCH70 120mm High Performance CPU Cooler
[/FONT][/COLOR][/B][B][COLOR=#434343][FONT=Arial]CORSAIR Professional Series Gold AX1200 (CMPSU-1200AX) 1200W ATX12V v2.31 / EPS12V v2.92 SLI Certified 80 PLUS GOLD Certified Full Modular Active PFC Power Supply
[/FONT][/COLOR][/B]**[COLOR=#434343][FONT=Arial]SAMSUNG 856 EVO 2.5" 500GB SATA III 32 layer 3D V-NAND Internal Solid State Drive[/FONT][/COLOR]**
```

I decided this week to upgrade to a NVME Samsung 970 Evo Plus drive. So I did this with a PCIe card. Last night I mounted it in the Motherboard, booted to Ubuntu 19 flash drive and installed with 0 issues.  Now, I knew my X58 bios would not boot the drive so I used Clover on a flash drive to boot into the new NVME card. Boots great, fast usage, very happy. Couldn't be more excited.

Now here is where I am stuck, per se.  I figured that if Grub can boot it after getting the hand off from clover, why couldn't grub on my 18.10 install on the SATA drive hand off the boot process?  So, I logged back into said SATA drive with 18.10 on it, forced grub to update, and low and behold it saw the 19.04 install and added it to the grub menu. HOWEVER, when I select it from the menu I get:

```
error: no such device: f7ed....too much to type, its the UUID 
error: file `/boot/vmlinuz-5.0.0-7-generic' not found
error: you need to load the kernel first
```

Now, a few things I've tried but could have been doing it wrong!  I edited the /etc/grub.d/40_custom file and added, WHAT I THOUGHT, would work copying the grub.cfg info from the one used in Clover, and then tried what seemed to work from the generated grub.cfg file used on the WORKING nvme drive's /boot/grub/grub.cfg file to boot. (I attached a image at the bottom of that relevant info I think). 

Again, this drive works, I used it last night getting my everyday items installed and its fast. Very happy with it. Booting using Clover as a hand off works, but is clunky, and just takes an extra step. I just do not see a logical reason why Grub cant do what I want it to. Any help, ideas, or suggestions are VERY welcomed.

---

### Post by oldfred on 2019-03-29
Have you updated UEFI/BIOS to latest version from Asus?
Is it really UEFI, even though many vendors still call it BIOS, or is it older BIOS only? I thought when Intel released i-series chips, motherboards became UEFI. But early UEFI implementations were not always the best, both vendors & operating systems.

Do not really know clover, but then I assume you are using BIOS/MBR configuration, not UEFI/gpt? Or even BIOS/gpt which is better than MBR?

This has not been updated to show all details on NVMe drives, but will show some info.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Perhaps some info here?
       
 x58-UD5 motherboard UEFI Windows 7 Jan 2015
[http://ubuntuforums.org/showthread.php?t=2259521](http://ubuntuforums.org/showthread.php?t=2259521)

Boot-repair uses bootinfoscript as first part of its report. I regularly run bootinfoscript as command line tool to document my configuration.
       Support NVMe and MMC devices bug oldfred request
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues) 
    I do not know NVMe drives and details, but one user posted changes required, I ran diff, and only a few lines.

---

### Post by Calandric on 2019-03-29
> **oldfred said:**
> .....


Thanks for the reply. Yes, BIOS only on that old X58 board, but still a rocking little machine. Just an update, I tried grub install on the /dev/sdb which is home to my 18.10 install, and update-grub to be safe (I thought) but I get to a grub rescue terminal on reboot, with the 'no such device' error as the cause. Clover will still boot the drives though so no big deal right now.

I'll check out the links you sent, still at work so I won't be able to do anything locally on the machine for a few hours but will return the summary reports you asked for when I can.

---

### Post by Calandric on 2019-03-29
Ok so I told a story. Got someone to reboot me back in.. Here is the boot-repair printout.

[http://paste.ubuntu.com/p/F585PF3RJQ/](http://paste.ubuntu.com/p/F585PF3RJQ/)

---

### Post by oldfred on 2019-03-29
I am confused.
Boot-Repair says it was booted in UEFI boot mode.
Are you booting Clover from your sdd in UEFI mode?

All your grub installs are BIOS boot mode. Clover may be able to reboot UEFI back into BIOS mode?

---

### Post by Calandric on 2019-03-29
Clover is simply a wrapper. Maybe not the right term. Its kind of like saying this:

Motherboard boots from BIOS to a usb stick that then acts as a UEFI emulator(?) which recognizes and boots the PCIe card which has a NVMe attached to it.  Best what I know to explain it.

[https://wiki.archlinux.org/index.php/Clover](https://wiki.archlinux.org/index.php/Clover)

So:

[LIST=1]
[*]Press Power button
[*]Hit f8 for boot menu
[*]Select USB stick with Clover on it
[*]Clover loads into a boot loader (EUFI bios emulator?)
[*]Select Ubuntu 19 NVMe m.2 PCIe card/hard drive
[*]Clover hands off to the Grub loader on that hard drive which was installed using the Ubuntu 19 usb install drive.
[*]Profit Happy Face, Happy Face.
[/LIST]

---

### Post by oldfred on 2019-03-29
Yes, now I remember what Clover is.
But it seems a long way around to boot an UEFI emulator to boot in BIOS mode.

Post this:
lsblk -f

Grub in sda is looking for an UUID that is not shown. May be UUID on NVMe drive which is not shown.

---

### Post by Calandric on 2019-03-29
> **oldfred said:**
> Yes, now I remember what Clover is.
But it seems a long way around to boot an UEFI emulator to boot in BIOS mode.

Post this:
lsblk -f

Grub in sda is looking for an UUID that is not shown. May be UUID on NVMe drive which is not shown.


```
beast@uBeast:~$ lsblk -fNAME        FSTYPE   LABEL              UUID                                 FSAVAIL FSUSE% MOUNTPOINT
loop0       squashfs                                                               0   100% /snap/discord/93
loop1       squashfs                                                               0   100% /snap/core/6673
loop2       squashfs                                                               0   100% /snap/gnome-3-28-1804/23
loop3       squashfs                                                               0   100% /snap/gnome-logs/57
loop4       squashfs                                                               0   100% /snap/gnome-calculator/352
loop5       squashfs                                                               0   100% /snap/gnome-3-26-1604/82
loop6       squashfs                                                               0   100% /snap/core/6531
loop7       squashfs                                                               0   100% /snap/gnome-characters/206
loop8       squashfs                                                               0   100% /snap/gnome-system-monitor/70
loop9       squashfs                                                               0   100% /snap/core18/782
loop10      squashfs                                                               0   100% /snap/gtk-common-themes/1198
sda                                                                                         
&#9492;&#9472;sda1      ext4                        bd7a5ba1-8b7f-4a13-812c-91103ea6848d                
sdb                                                                                         
&#9492;&#9472;sdb1      ext4                        dfc2c045-bb2f-48b7-87e6-4b2909b6d792  157.6G    60% /media/beast/dfc2c045-bb2f-48b7-87e6-4b2909b6d792
sdc                                                                                         
&#9500;&#9472;sdc1      ntfs     System Reserved    622429AB24298361                                    
&#9492;&#9472;sdc2      ntfs                        68702B40702B13FA                      327.9G    30% /media/beast/68702B40702B13FA
sdd         iso9660  Ubuntu 19.04 amd64 2019-03-25-07-57-25-00                              
&#9500;&#9472;sdd1      iso9660  Ubuntu 19.04 amd64 2019-03-25-07-57-25-00                     0   100% /media/beast/Ubuntu 19.04 amd64
&#9492;&#9472;sdd2      vfat     Ubuntu 19.04 amd64 0167-A37B                                           
sde                                                                                         
&#9492;&#9472;sde1      vfat                        AAC9-392D                              14.9G     0% /media/beast/AAC9-392D
nvme0n1                                                                                     
&#9492;&#9472;nvme0n1p1 ext4                        f7ed8ce6-374e-439c-85e1-ec8c33a3ec92  350.4G    18% /
beast@uBeast:~$ 

```

EDIT:  Installed grub via boot-repair on all drives, no change.

---

### Post by oldfred on 2019-03-29
Your grub in sda is looking for 280fccb1-84de-494d-bb77-731d5b0fc840 but you do not have that UUID, must be left over from old install that got reformatted.
If you reinstalled grub with Boot-Repair it should have installed one grub to every MBR. 

But if you have multiple installs better to have different grub installs in each MBR. You can do that with Boot-Repair's advanced mode and choose an operating system and a MBR, usually same drive as install.

---

### Post by Calandric on 2019-03-29
> **oldfred said:**
> Your grub in sda is looking for 280fccb1-84de-494d-bb77-731d5b0fc840 but you do not have that UUID, must be left over from old install that got reformatted.
If you reinstalled grub with Boot-Repair it should have installed one grub to every MBR. 

But if you have multiple installs better to have different grub installs in each MBR. You can do that with Boot-Repair's advanced mode and choose an operating system and a MBR, usually same drive as install.

Yeah i dunno how that drive got Grub on it to begin with, but to be safe I updated Grub on Every drive, but still got he same errors.

---

### Post by oldfred on 2019-03-30
Are you able to check if firmware on SSD is up to date.
Many users with SSD issues update firmware and solve issues. Even new drives.

---

### Post by Calandric on 2019-03-30
Thanks for all your help.  

I checked Samsung website; the only software downloads for the 970 EVO Plus is drivers for windows. The only firmware updates do not pertain to this drive. So too properly answer your suggestion, no, there isn't any firmware updates available. 

I noticed poking around with grub rescue command prompt, most of the "ls (hd3,msdos2)/” etc return "unknown filesystem" errors.  Only the windows install, and the Ubuntu 18 drives report back properly. 

I noticed when updating grub for the 19 nvme install grub reports "efi configuration saved" or something like that. Being my motherboard is BIOS and not UEFI the culprit and can that be altered to use a BIOS config?

---

### Post by oldfred on 2019-03-30
The Samsung site has Magician for firmware updates.
[https://www.samsung.com/us/support/owners/product/970-evo-nvme-m2](https://www.samsung.com/us/support/owners/product/970-evo-nvme-m2)
I had found under commercial support a Linux version, but never got it to work for my old SSD. And I do not have Windows.

Because of Clover & system looking like UEFI, grub may be confused?

---

### Post by Calandric on 2019-03-30
That may be but why would that matter if booted normally under the 18.10 drive? 

Let's consider for a moment, taking clover out of the equation all together.  When boot normally into 18.10 I can mount and browse those files without issue.  When I update the kernel and grub updates it finds the 19.x drive and adds it automatically.  However,  rebooting and selecting that install yields the original errors.

---

### Post by oldfred on 2019-03-30
Can you use a configfile to load 19.04 install?
I also now like to use labels.

I installed disco, labeled partition and added this to 40_custom.

      ```
 menuentry "Ubuntu 19.04 Disco  (on /dev/sdb8)" {

 set root=(hd1,gpt8)
search --set=root --label disco --hint hd1,gpt8
configfile /boot/grub/grub.cfg 
 } 
```    

Not sure if NVMe if hint then is nvme0 and partition is p1? as drive/partitions with NVMe are nvme0n1 for example.

---

### Post by Calandric on 2019-03-30
I'll try that tomorrow. My biggest unknown to that code is that I get "unknown file system" errors on some of my drives when trying to ls the (hd4,1)/ for example. May just have to write them all down and just try the partitions one by one. 

Never the less,  will try some more tomorrow.  Brain not firing on all eight at the moment.

---

### Post by Calandric on 2019-03-31
Device not found and unknown filesystem.  Grub can not see my nvme hard drive.  All the (hdX,msdosX) listed either return my other hard drives or unknown file systems. Comparing partition counts against the hard drives I have I deduce it is not being found in the grub rescue console.

---

### Post by oldfred on 2019-03-31
It should be using UUID, but NVMe is not sda, or hda, but nvme0n1 and partition is p1.

Does this work from grub command line as I do not know NVMe well and then how grub sees it?
ls (nvme0n1,p1)

---

### Post by Calandric on 2019-03-31
[COLOR=#000000]ls (nvme0n1,p1)  and any variance there of returns unknown disk. [/COLOR]

---

### Post by oldfred on 2019-03-31
Is that at grub or Ubuntu terminal. It only may work in grub terminal as it uses a different format for ls command.

---

### Post by Calandric on 2019-03-31
> **oldfred said:**
> Is that at grub or Ubuntu terminal. It only may work in grub terminal as it uses a different format for ls command.

grub rescue terminal

---

### Post by oldfred on 2019-03-31
I am out of ideas.
It just seems grub does not want to see your NVMe drive.

I used a standard SATA SSD without issue on my old BIOS only system in 2011. It was a low cost OEM Microcenter 60GB just for / (root). But improved my old BIOS system enough that I put off buying a new system for 3 years.

---

### Post by Calandric on 2019-03-31
Yeah I have 0 issues with any other hardware/setups/etc I have ever used. And like I've said, I boot just fine with clover, just wanted to cut out the middle man so to speak.

---

### Post by Calandric on 2019-04-03
[FONT=&amp]!!!!!!!!!!!PROGRESS UPDATE!!!!!!!![/FONT]
[FONT=&amp]
[/FONT]Hope you aren't offended Fred, but I went seeking more insight after our conversation hit a hurdle..  Over on the Ubuntu Reddit I offered up the same series of situations and questions with the findings you and I discussed, and one person offered up trying gpt partitions instead of mbr and sure enough, Grub can now see my nvme drive using ls (more on that in a minute).  Suggestion #2 was to put grub on a separate drive, a regular SATA drive that BIOS can see. Which I did, which leads me to this...

[FONT=&amp]Ok! So we have progress. Reinstalling has yielded new things. Trying to boot to the SATA drive/partition that I told ubuntu to install boot on just gives me a blinking _ and never moves from there. So I tried some things, one of which was using clover again for rescue but it didn't work. HOWEVER I did find that changing to gpt drives shows up now in grub! So, I did the following at the grub> prompt:
[/FONT]
```
set prefix=(hd0,gpt1)/grub (this is the SATA drive, 1024mb GPT partition)
set root=(hd1,gpt1)
insmod linux
insmod normal
normal
```

[FONT=&amp]And TADA! We booted. YAY! But why? Why didn't the drive boot into grub on its own without help?
[/FONT]
[FONT=&amp]So, I rebooted and booted into another drive (/dev/sdb) that has ubuntu 18.10 on it. I told grub to update, and then rebooted again. When grub came up on that drive (18.10), I tried the NVMe drive we just re-installed 19 on....IT BOOTED. Yay![/FONT]
[FONT=&amp]
So now what? What is wrong that grub won't boot on its own, yet boots with those commands from the grub> command prompt?[/FONT]

---

### Post by oldfred on 2019-04-03
Any useful info is good info, no matter source. 
And I regularly read other posts, mostly in forum to update my notes.

I always recommend gpt, it almost is required with UEFI, but Ubuntu will install to MBR in UEFI mode. Windows requires gpt for UEFI and UEFI highly recommends gpt.
Back with that new SSD in 2011 I converted to only using gpt on all new & reformatted drives. But BIOS boot requires a bios_grub partition on gpt drive for grub's core.img that normally goes just after MBR in MBR partitioning. With gpt that space does not exist so it needs the bios_grub partition.
When Windows required UEFI/gpt in 2012, I started adding the ESP - ESP system partition to all new or reformatted drives, so I could move drive to new UEFI system.
Or surprised I did not suggest using gpt since using Clover. Not sure if Clover requires it or not. But UEFI needs ESP and BIOS needs bios_grub on gpt drives. 
I used to always add both ESP & bios_grub to every drive including larger flash drives.

So is the only thing not working directly boot from SSD? 
Perhaps a BIOS thing where it will not boot from your configuration? Does BIOS show drive correctly in list of drives?
Some with external drives or particularly where they replace DVD caddy in laptop with second drive often have boot issues like this. While DVD will boot, drive in caddy will not boot. All boot files  (at least grub and maybe /boot) have to be on internal drive, but rest of install can be on drive in caddy.

---

### Post by Calandric on 2019-04-03
Yes, the drive shows properlly in BIOS menus and configs.  When I partitioned/formatted ALL I did was create the gpt partitions using gparted prior to booting the install disk. So when it came to the install setting up partitions I selected that 1024mb partition, told it to use this partition, ext4 file system, and mount it at /boot.  Then selected the nvme drive and told it to use it, and mount it at /.   

How do I check for "bios_grub" partition? How should I go about creating it now post install?

---

### Post by oldfred on 2019-04-03
For grub to correctly install to gpt drives is needs a bios_grub partition.
It is 1 or 2 MB unformatted with bios_grub flag anywhere on drive (actually must be inside first 2TiB).
I typically make first partition an ESP (FAT32) and second partition a bios_grub.

Old listing from bootinfoscript report. My new system only has ESP.
```
GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,026,047     1,024,000 EFI System partition
/dev/sda2             1,026,048     1,030,143         4,096 BIOS Boot partition
/dev/sda3             1,030,144    52,229,362    51,199,219 Data partition (Linux)
```

---

### Post by Calandric on 2019-04-03
> **oldfred said:**
> For grub to correctly install to gpt drives is needs a bios_grub partition.
It is 1 or 2 MB unformatted with bios_grub flag anywhere on drive (actually must be inside first 2TiB).
I typically make first partition an ESP (FAT32) and second partition a bios_grub.

Old listing from bootinfoscript report. My new system only has ESP.
```
GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,026,047     1,024,000 EFI System partition
/dev/sda2             1,026,048     1,030,143         4,096 BIOS Boot partition
/dev/sda3             1,030,144    52,229,362    51,199,219 Data partition (Linux)
```


Forgive me, but I'm going to be straight with you. Partitioning and all that most of the time confuses me.  If you can think of a guide or tutorial somewhere for me to fix my boot partition/drive please slap me upside the head with it. I follow instruction very well. For your consumption here is my updated drive scheme. 

 [http://paste.ubuntu.com/p/qVwmv24PFS/](http://paste.ubuntu.com/p/qVwmv24PFS/)

/dev/sda is 750gb storage device. 
/dev/sdb  is is fallback WORKING 18.10 install
/dev/sdc is my boot drive. sdc1 is boot partition and sdc2 is just future storage/empty atm so I can start this drive over to fix my boot issues if I have to. 
/nvme0n1 is of course the NVMe drive w/ 19.10 on it

---

### Post by Calandric on 2019-04-03
Is this what you meant?  If so once I've edited the partition layout, do I need to change anything within grub? update-grub or anything like that?

---

### Post by oldfred on 2019-04-03
Most installs do not need /boot partition which must be ext4.

But the bios_grub is only 1 or 2MB and must be unformatted. You can shrink any partition by 3 or 4MB as you have to have some sectors between drives.

Because it is unformatted gparted will show it with a warning flag. It really should not as a bios_grub partition in gpt has a valid unique GUID.

---

### Post by Calandric on 2019-04-03
Thanks again for all your time. What I had didn't work, I still just get the blinking _. I am noticing mine says 'unallocated' where yours says 'unknown'  so I'll need to correct that somehow.

In the meantime, while I was at home for lunch trying my change I went ahead and grins & giggles tried something else. I ran ```
install-grub /dev/sda
``` on my old SATA3, 750gb storage drive located at /dev/sda. Then ```
update-grub
``` before rebooting again and at my boot manager selected that drive and poof, we booted to 19 properly as it should. 

Now I could stop here and call it a day. But I wouldn't learn anything if I did that, I plan to continue this mission and figure out 'your way' so to speak. I'll report back when I figure out how to make that partition 'unknown'.

---

### Post by oldfred on 2019-04-03
You are also showing sdc as gpt now.
So the only grub that should work are the MBR drives sda & sdb.
You should be able to add a bios_grub partition to sdc and install its grub to MBR of sdc.

With multiple drives never use Boot-Repair's autofix. that will install one grub to the MBR of every drive. You want each drive to have a different grub and normally the grub from the install on that drive. In Boot-Repair's advanced mode is the option to select an install and a drive. Always use that.

Then any grub should be able to boot all the other systems, either directly, with chainload to MBR of another drive, or configfile to use other install's grub. Lots of ways.

---

### Post by Calandric on 2019-04-04
Thank you so very much sir for your help. After several hours of failure trying to do this quickly I decided to take what I now know and start over. I'm happy to report everything is perfect. 

I'll update this thread in the morning and mark it solved along with detailed explanation, steps, and logic for future folks like myself. Thank you so much again for your time and insight!

---

### Post by Calandric on 2019-04-04
Link to reddit post: [https://www.reddit.com/r/Ubuntu/comments/b8k1pd/nvme_pcie_card_grub_problems/](https://www.reddit.com/r/Ubuntu/comments/b8k1pd/nvme_pcie_card_grub_problems/)

My working setup:

[COLOR=#000000][FONT=Arial]So, taking what -I- learned from some good folks here (This means you Fred) and a couple guys input over at the r/Ubuntu reddit page I have finally figured this out. What might have been common sense knowledge to some escaped me until now. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The solution was to have a separate /boot partition on a ye ol’ standard SATA disk drive that was seen by old school BIOS. This drive was setup as a **GPT** partition table, and formatted like so:
[/FONT][/COLOR]```

Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1075MB  1074MB  ext4               legacy_boot
 2      1075MB  1085MB  10.5MB                     bios_grub
 3      1085MB  500GB   499GB   ext4

```

[COLOR=#000000][FONT=Arial]You have partition **1** for your /boot files. I chose 1gb in size, obviously you could use smaller, but for future usage sake, I went overboard. This was formatted with ext4 file system. You have to set the ‘boot’ flag on this partition as well. I did NOT use gparted to do that, because when I did it automatically forced **ESP** as well. This MAY be ok, I do not know. I used the “DISKS” program that comes standard on ubuntu installs. Select the drive in the LEFT pane, then the partition in question (Partition 1) and under the settings for it, set **”LEGACY BOOT”**  NOTE again ESP may be ok I do not know.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]For partition **2** you need an UNFORMATTED partition. Obviously it doesn’t have to be large, mine is only 10MB. Be careful here, this is where I originally got confused. GPARTED should report the partition as UNKNOWN with a red warning image. I achieved this by choosing **FORMAT -> CLEARED**.  DO NOT FORGET to set the **”bios_grub”** FLAG on this partition. Its purpose boggles my mind, but it works.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Finally, for partition **3** I just formatted the remainder of the drive as ext4 for general usage. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The Partition table of the NVMe must be **GPT** as well, or as we’ve found, can not be seen by grub. Bug maybe? Who knows, but GPT works.
[/FONT][/COLOR]
```
Model: Samsung SSD 970 EVO Plus 500GB (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End    Size   File system  Name  Flags
 1      1049kB  500GB  500GB  ext4

```


[COLOR=#000000][FONT=Arial]Nothing special there, just be sure the partition table is **GPT** the installer does the rest.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Now, during install when it asks what to do about where to install/partitioning/etc. You want to choose **SOMETHING ELSE**.  You want to RIGHT click on the partition you made on the standard SATA drive, Partition 1, and tell the installer to use this partition. Set the MOUNT POINT to /boot. Finally click the “FORMAT” box to the side of that partition as well. May not have to, but the installer warns, whines, and complains so I did it anyway.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Second, you want to select the NVMe partition you created, and right click to set it as use this partition, and set the mount point to **/**. Also tick the FORMAT box to the side of this partition so that the installer stops its whining and complaining.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Last but MOST CERTAINLY not lease, the very bottom selection, you want to tell the installer to install grub on your SATA drive. [s]I will admit, I can not recall if I installed to /dev/sdc or /dev/sdc1 as I was exhausted and could not have cared less if it worked or not by this point. If someone could correct me here I would be much obliged. Otherwise you just close your eyes and try one, and if it didn’t work, try the other.[/s]  **--EDIT-- Fred confirmed I had to have chosen /dev/sdc in this field. Thanks Fred! **[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Either way, after the install has completed and PC restarted I went into the BIOS configuration and set my SATA (/dev/sdc) as the primary boot device. To my surprise and joy I saw Grub. I was numb at this point. However when it booted and I realized it booted the correct, fresh install of ubuntu, I was quite satisfied. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]As I’ve stated, I do not pretend to be an expert, just someone capable of learning well and quickly. If ANYONE has any comments or suggestions to add or correct me on, PLEASE, feel free to do so and I’ll gladly amend my post of suggested steps. Thank you again to everyone who contributed to helping me achieve my goal. :D[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by oldfred on 2019-04-04
All gpt partitioned drives need either an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot. 
I like to include both on even drives that are primarily for data, just in case in future I want an install on that drive.
Grub will not correctly install in BIOS mode to any gpt drive without a bios_grub.
Ubuntu's UEFI installer only installs to first ESP, usually sda or first NVMe drive. But other Linux may install to an ESP on another drive if specified.

You must have specified a drive like sda or sdc, not a partition like sdc1 to install grub during Something Else. Grub2 does not like to install to a partition, and cannot be directly booted from a partition boot sector, only from MBR in BIOS mode. Only if you have another grub in a MBR may an install to a partition work, but not recommended.

It has to be something about your UEFI/BIOS and NVMe drive configuration that requires boot from a SATA drive. Most can boot directly from NVMe drives, but some early UEFI needed UEFI updates. And normally motherboards that have NVMe drives have UEFI with support for booting NVMe drives.

Glad you found work arounds to make it work on your system.

---

### Post by Calandric on 2019-04-04
> **oldfred said:**
> 
You must have specified a drive like sda or sdc, not a partition like sdc1 to install grub during Something Else. Grub2 does not like to install to a partition, and cannot be directly booted from a partition boot sector, only from MBR in BIOS mode. Only if you have another grub in a MBR may an install to a partition work, but not recommended.
.

Thanks for clearing that up! Also, I have a BIOS only system. X58 chipset from ~2010 era that does not support ONBOARD M.2 drives, or booting from a PCIe adapter, this is why the work around was needed. :D

Thanks again for all your help!

---

### Post by koby-ryu on 2019-12-05
I had the same problem as [**[COLOR=#000000]Calandric[/COLOR]**]("https://ubuntuforums.org/member.php?u=1127169"),  his solution fixed my problem. Thanks bro!

---

### Post by marco-ernst on 2020-02-10
Hey Guys,
I have the same problem and was struggling with it for a hole day. When I saw your thread I wanted to create an account here just to say thank You. But when I follow your instructions, the Linux Mint installer warns me that there is no EFI-partition and that the boot will likely fail. But even the install fails with the package grub-efi-amd64-signed not installing. Ubiquity hangs completely after that.

---

### Post by oldfred on 2020-02-10
@marco-ernst
Best to start your own thread & since Mint in the MINT sub-forum. Mint may not be the same as Ubuntu.
But as posted above you have to have an ESP to install in UEFI boot mode.
But if you also have Windows, you really need to install in same boot mode or re-install Windows in UEFI boot mode.

In your new thread post this:
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by marco-ernst on 2020-02-10
O.k. Got it working.
Just made a third partition dedicated to boot. In addition to the 2 mentioned by Calandric I did a ESP on the SATA Drive. Installer happy, boot happy, me happy.
Just wondering how You guys got it to work without that third one. 

Anyway: Thanks a lot, peeps!

---

