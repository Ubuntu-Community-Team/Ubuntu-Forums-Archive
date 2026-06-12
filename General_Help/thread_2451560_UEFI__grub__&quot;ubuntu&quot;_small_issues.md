---
title: "UEFI / grub / &quot;ubuntu&quot; small issues"
date: 2020-10-05
forum: General Help
---

### Post by helen314 on 2020-10-05
Perhaps somebody could be re-educate this group , me  included , how it all fits together. 
( It has been an ":issue" since I first loaded Ubuntu...) 

so here is my view , no particular sequence , just my opinions:
1. There is no BIOS
2. Instead of BIOS there is so0mting called UEFI  / EFI (?) - or "hardware setup."  
3. Initially my hardware came with "default  EFI" 
4. Part of the EFI is "boot sequence " - NOT BIOS! 
5. After initial Ubuntu install my "default" boot sequence was titled "Ubuntu" ?
6. After my :setup" is done I get to see "grub"  which would NOT be seen if I had SINGLE boot system!
7. I can select  actual 'boot" process / OS in "grub"  or let it process the mystery "Ubuntu "  - as optioned in my "UEFI" setup.

As far as i know - there  should be ONLY ONE grub file in the system and putting in on USB should be fine.

---

### Post by oldfred on 2020-10-05
UEFI has a default menu entry and even old BIOS had a default on which drive you could boot from.
To see boot order with UEFI:
sudo efibootmgr -v

Grub has a default boot entry and if only one install, will not normally show menu, just boot that one entry. You have to press escape key just after UEFI/BIOS screen but before grub. If UEFI fast boot on, you may not have time to press a key and have to do a "cold" boot or full power shutdown.

UEFI currently has CSM, but future proposals discuss eliminating CSM on new systems.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

When Apple converted to Intel chips, it also used Intel's EFI. Then Intel turned EFI over to a separate group and it was UEFI v2 and old EFI became v1.
Microsoft required vendors to install Windows 8 in UEFI boot mode to gpt partitioned drives in 2012. So most hardware is UEFI based.

Lots more info & links to details at end of my post linked below in my signature.

---

### Post by helen314 on 2020-10-06
While troubleshooting unrelated problem I am back to the ancient , never satisfactory answered , issues. 

My system starts  with UEFI setup - not BIOS. 
I have an access to "boot menu" - via F11 . 
One of the items in  such menu in named "ubuntu". 
My wild guess it is related to "grub". 
I am presently limping along with booting from USB drive - painfully slow process - but 
I get to "grub" options eventually , however, the USB drive is not there. 
In theory - only time I should end with ":grub" when I have a mutiboot system. 
For safety reasons I disabled my SATA controller , have no other  USB EFI boot enabled drives and still getting this inaccessible OS  option 
in "grub". 

Who creates "ubuntu"  (label?) and why?
How does "default UEFI " works , especialy with "grub"  ? 
When I enable "USB" in my UEFI setup - why "default UEFI " option does not identify my USB drive ?
(Yes, my 2nd partition in USB drive is /boot/efi  and it boots , slow , but surely. )

And last - the F11 access to boot menu is nice but how the heck I clear it - it keeps growing with non existent hardware... 

Thanks 
Cheers

---

### Post by oldfred on 2020-10-06
You asked similar question in another thread that really should have been here anyway. 
Moved that question & some info to this thread.

Post this:

sudo efibootmgr -v

What brand/model system?

---

### Post by helen314 on 2020-10-06
To see boot order with UEFI:
sudo efibootmgr -v

That is basically what I get after pressing F11 - and it includes the "Ubuntu" - which is , as far as I can tell - access to grub. 




Sorry "oldfred"  the original post was a reply in another thread and it got no response. 
I am not in habit to hijack so I posted my own. 

BTW I may be inclined to mark post solved when it is. 
Thanks  for asking.

---

### Post by oldfred on 2020-10-06
The command efibootmgr  with the -v shows lots of details. We need to see that.
Grub install uses efibootmgr to create new "ubuntu" entry.

See also the man page on efibootmgr for details.
man efibootmgr

---

### Post by grahammechanical on 2020-10-06
For information. 

BIOS = Basic Input/Output System. It is information stored on an integrated circuit chip that informs the motherboard what kind of computer it is. It is a settings utility for the motherboard that can be modified to account for different hardware connected to the motherboard.

The BIOS setting utility has been replaced with a Unified Extensible Firmware Interface (UEFI) settings utility. 

[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

I have some questions. Did you install Ubuntu on the hard drive? If so, that would be how the Ubuntu boot option was entered into the UEFI settings utility. Disabling the Sata controller will prevent UEFI from passing the boot process on to the Grub bootloader which has its core code and other data stored on the Sata hard drive. This is why you are getting the "Inaccessible OS" message.

On the other hand, if Ubuntu is installed on a removable USB drive then the Ubuntu entry in the UEFI may not be pointing to the USB drive and that is the reason for the Inaccessible OS message.

I do not have a UEFI motherboard. So I cannot explain how to edit the entries in UEFI. The motherboard manufacture should provide information on how to do that. 

Regards

---

### Post by helen314 on 2020-10-07
Good and bad news 
I am writing this while installing clean Ubuntu  onto USB "stick"' drive - hopefully with UEFI boot partition. Painfully slow process. 
AFTER I can successfully boot using  this USB drive I am going to repeat installation and attempt to install NEW OS onto drive I cannot currently boot from (missing UEFI boot partition) AND hopefully KEEP the existing partitions and data. 

I am believe that my problem started with UEFI setup - it was cluttered with so many boot options, but now it is pretty clean.


However - I probably had an issue with mixing "legacy USB" with UEFI  , I have USB3 drive too. 
Like to know what is "legacy USB"  , my guess it boots via BIOS .


Good point about disabling SATA , however since I had boot-able USB grub should have caught that.
BUT - there should be ONLY ONE grub and I have no idea on which device it resided. Maybe in future I'll make sure to have groub on physically accessible USB .
I keep my USB disks out of sight. 


Interesting note - after specifically disabling the UEFI "fast boot mode " after restart it is back to "fast boot mode "....
PS It has been installing for over an hour ... time for coffee

---

### Post by oldfred on 2020-10-07
Full install to USB flash drive is slow. 
You probably will get grub installed to ESP on internal drive.
Ubuntu's Ubiquity only installs grub boot files to first drives ESP - efi system partition. That normally is the Windows drive. 
While that will be bootable, it only boots with flash drive plugged in. 

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

### Post by helen314 on 2020-10-07
It's going....
Here is my real concern, but from years of experience this is pretty normal. 
Installing SINGLE OS is pretty starlight forward...
Running a SIMPLE application is no breiner either. 

Building mutiboot system gets unnecessary complex - see few posts about dual boot Windows and Linux..

Replacing BIOS with UEFI when each vendor implements it his way is a disaster..

Mixing USB (versins) with SATA where boot priorities are "by guess by golly " lead to my problem.

Adding more that one RADI5 array - mixing USB abd SATA is no fun 

BUT when "grub" ends in "limited edit mode "  one is stuck
When "grub advanced recovery mode" ends in "welcome to emergency recovery "  - one ends up "try this , try that ..." 

Moral of (my) story when boot does not complete next best step is to do is 
 the old "if MS designed cars... roll all windows down and restart " -- or get an new computer.

---

### Post by helen314 on 2020-10-07
Another dead end. 
Installing another bootable  OS (16.04.7)  ,"alongside" of existing non bootable version. 
Getting stoped by an  error " partition sectors exceed msdos allowable size ..." 

1, Which partition ???
2. It is 2020 and Ubuntu install stops because "msdos"  size limits ?

Question 
If i install  latest  version of Ubuntu , just to be able to boot the drive 

WILL i BE WASTING MY TIME AND GET SAME "MSDOS" ERROR ?

I have 3TB drive .... iI need to recover.

---

### Post by oldfred on 2020-10-08
MBR(msdos) was designed in early 1980's when GB was huge and unheard of. So they set a hard limit on MBR partitions of 2 TiB.
So if using a newer drive over 2 TB, you need to use gpt partitioning.
And then better to use UEFI, but can use the old BIOS boot.

IF UEFI, you need gpt and an ESP.
IF BIOS on gpt drive, you need a bios_grub.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Please review all the info I have posted in the link below in my signature.
Some is a little too much for a beginner, but you need to learn a lot of it.

---

### Post by helen314 on 2020-10-08
I am really not ready to discuss DOS , and reluctant to SPECIFICALLY point out that:
1. I was using recent ISO  to install Ubuntu 
2. The error gives no clue info WHICH partition is the "problem" 
3. There is no option to bypass the error, hence the install fails.  

It has been my experience that when a tool does not work and SPECIFIC info is posted it often results in 
banning the poster....
So let it go...

I am presently able to boot via recent clean install , however, I have to use "advance recovery "  ( grub) and then go into "maintenance mode " , and then run "clean"...
Dunning "clean"  actually runs "update" and it ALWAYS rebuilds "grub" ,

BUT  UEFI  does not pass / gets or whatever to use newly configured "grub"  until full power down / up...

So the new grub cannot be used "normally"  as far as UEFI  is concerned (?)  , UEFI  then put "grub" into "limited edit mode " . 
Since I have no idea or want to find out WHY UEFI doe not find valid boot , I end up with  "exit" from this edit mode. 




Interestingly - found out , it was on the bottom of page and I needed to scroll into it, the UEFI  has up to 3 attempts to boot and if it fails it AUTOMATICALLY restore UEFI  setting to ALL default. 

Nice, but system will not come up after power down  - because the default is - DISABLE - start up on power -up  !

---

### Post by CelticWarrior on 2020-10-08
> [COLOR=#000000]So if using a newer drive over 2 TB, you need to use gpt partitioning.[/COLOR]


You have a 3TB drive so the error is obviously there.
Additional info: The Ubuntu installer can do pretty much everything regarding the partition management - create, delete, etc. - but it CAN'T change the partitioning type like you need to from MBR ("msdos" - not necessarily related to the old OS with the same name although it was with that one it started) to GPT. You need a tool like GParted to do that and you can use GParted in a live session. Select the drive in question then Devices menu > New partition table > select GPT. Please note this will erase everything in that drive.

---

### Post by helen314 on 2020-10-08
> **CelticWarrior said:**
> You have a 3TB drive so the error is obviously there.
Additional info: The Ubuntu installer can do pretty much everything regarding the partition management - create, delete, etc. - but it CAN'T change the partitioning type like you need to from MBR ("msdos" - not necessarily related to the old OS with the same name although it was with that one it started) to GPT. You need a tool like GParted to do that and you can use GParted in a live session. Select the drive in question then Devices menu > New partition table > select GPT. Please note this will erase everything in that drive.

Still getting of the original post. 
I have working , UEFI bootable 3TB  drive with an extended partitions and unused partition. 
For refresher - the installation failed because of "DOS" sectors , give me no indication which partition was failing and NO way to recover. End of story. 
PS I have been using gparted for years, thanks for refresher course. Seen my next post.

---

### Post by helen314 on 2020-10-09
If it is OK with management, I like to get back to "small issues". 
1. I can boot , however, only using this convoluted approach 
a. My UEFI system setup opens "grub" file - even when there is only ONE OS to access 
b. I have to select "Advanced..."  - letting "ubuntu" options leads to further complications ( still waiting for somebody to explain what "ubuntu" (file) came from - it is part of UEFI setup boot sequence ) 
c. Then I have to pick '..recovery "   - I have two "versons" to pick from 
d.Watching the progress - BTW I see ".../boot /efi "  - see further  down the post .
e. Then I get basic text options - to boot I selece "resume "
f. The I get a message blah  blah and click OK 
g. I can onserve rmore progress and then finally see "desktop". 

I have no idea why letting "grub" time-oiut and run "ubuntu" (file ) DOES NOT  do the job SAME as me doing it manually. 
That is of minor issue. 


I am using dmesg to fix these issues .

2. Here is the first RED entry in dmesg

 Couldn't get size: 0x800000000000000e
[    1.893012] MODSIGN: Couldn't get UEFI db list
[    1.894908] Couldn't get size: 0x800000000000000e

Any idea how to fix this ?


3.grub configuration file is GENERALLY updated after OS "update" 


1. The only image which SHOULD automatically boot is 
Found linux image: /boot/vmlinuz-4.15.0-118-generic

 Found initrd image: /boot/initrd.img-4.15.0-118-generic
2. The images is can use in "advanced recovery "  are 

Found linux image: /boot/vmlinuz-4.15.0-118-generic

 Found initrd image: /boot/initrd.img-4.15.0-118-generic

 Found linux image: /boot/vmlinuz-4.15.0-45-generic
3. These entries are what I need to boot with
to recover my data 


Found Ubuntu 16.04.6 LTS (16.04) on /dev/sda6

 Found Ubuntu 16.04.6 LTS (16.04) on /dev/sdb2
 Found Ubuntu 16.04.2 LTS (16.04) on /dev/sdb5
 Found Ubuntu 16.04.7 LTS (16.04) on /dev/sdc4
 Found Ubuntu 16.04.7 LTS (16.04) on /dev/sdf2


Any idea HOW to make them usable / visible ?

The requirement is NOT to implement any methods which would destroy the ANY data . 






 Found initrd image: /boot/initrd.img-4.15.0-45-generic
 [QUOTE
                        Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-4.15.0-118-generic

 Found initrd image: /boot/initrd.img-4.15.0-118-generic

 Found linux image: /boot/vmlinuz-4.15.0-45-generic

 Found initrd image: /boot/initrd.img-4.15.0-45-generic

 Found Ubuntu 16.04.6 LTS (16.04) on /dev/sda6

 Found Ubuntu 16.04.6 LTS (16.04) on /dev/sdb2
 Found Ubuntu 16.04.2 LTS (16.04) on /dev/sdb5
 Found Ubuntu 16.04.7 LTS (16.04) on /dev/sdc4
 Found Ubuntu 16.04.7 LTS (16.04) on /dev/sdf2
 Adding boot menu entry for EFI firmware configuration
 done
  ][/QUOTE]

4. I need an assistance with activating SPECIFIC RAID .
I can see (in dmesg) that the array is being operated on, however, 
I can "stop" it , but when I "assemble" I get  " no entry in config".
[COLOR=#ff0000]**HOw do I configure the existing array without destroying the contents?**[/COLOR]
When I attempt to "move" one device to another , running  array, I get 
"can't do , device is busy ". 

Cheers

---

### Post by oldfred on 2020-10-09
Have you converted your 3TiB drive to gpt. 
That is a main part of your many errors.
Windows only lets you boot in UEFI mode from gpt drives.
And all drives over 2TB must gpt, or you have converted drive from 3TB to 2GB with MBR(msdos) partitioning.

The modsign error/warning many get. I believe you just ignore it. 
Something related to UEFI and UEFI secure boot.
Is your UEFI updated to most current version?

---

### Post by oldfred on 2020-10-09
Post this:
sudo parted -l

With UEFI systems, you really should only use gpt partitioning.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by helen314 on 2020-10-09
[QUOTE=oldfred;13991517]Have you converted your 3TiB drive to gpt. 
That is a main part of your many errors.
Windows only lets you boot in UEFI mode from gpt drives.

I am not using Widoze. 
Before this crash I was happy to boot from ANY size of disk, USB or SATA. 

And all drives over 2TB must gpt, or you have converted drive from 3TB to 2GB with MBR(msdos) partitioning.

How do I verify GPT  and why ?  The 3TB and only bootable drive has EFI partition - no MBR 

The modsign error/warning many get. I believe you just ignore it. 
Something related to UEFI and UEFI secure boot.
Is your UEFI updated to most current version?

All these years I have not  bother to have make my setup having access to network.
Did not need to have "the latest version"  when it run mutiboot just fine. 
And I do not know HOW to update UEFI firmware AFTER my PC is running. 

{/QUOTE]

Can anybody help me to get out off this "windows centrik mode " thread and help me to activate OTHER bootable drives?
I am using 3TB as bootable  because UEFI /grub said so and  it has plenty of unused space, that all.

---

### Post by helen314 on 2020-10-09
Linux doc  is very clear about setting ESP flag 

[https://www.linux.org/threads/gparted-partition-and-filesystem-flags.11640/](https://www.linux.org/threads/gparted-partition-and-filesystem-flags.11640/)

---

### Post by CelticWarrior on 2020-10-09
> [COLOR=#000000]How do I verify GPT and why ? The 3TB and only bootable drive has EFI partition - no MBR[/COLOR]


This is a misunderstanding.
The presence of an EFI **partition **says nothing about the **partitioning type**. You can have any type of partition, including ESP, in a "msdos" partition table. The problem with "msdos"/MBR and the cause of the issues you're having is the size limit for a single partition as explained before, as well as the distinction between primary, extended and logical partitions and the limitation to four primary partitions not so relevant here but something to account for. That's why you need [GPT]("https://en.wikipedia.org/wiki/GUID_Partition_Table") for a 3TB drive. Something already explained many times already and with supporting links. 

> [COLOR=#000000]And I do not know HOW to update UEFI firmware AFTER my PC is running.[/COLOR]

The motherboard's firmware - BIOS or UEFI - is something that often requires updates and it always was. If you're installing OSes then that's something you should account for, get familiarized with, check the motherboard's manufacturer's support pages, read the changelogs to understand what has been added and/or fixed vrom one release/version to another, and, of course, understand and use the available methods to install a new version whenever necessary (it OFTEN is, period).


It seems to me that you think you know a lot more than you actually do. That is detrimental to your ability to learn what you need to learn to fix the issues by listening to others and the quite unpleasant attitude that comes with the "I know better" arrogance detracts others from helping you further.  So I suggest you take a break to read what have been posted already in order to understand 1) what you need to do to any 2TB+ drive regarding partitioning type (GPT) and 2) understand the hardware/firmware interaction and WHY sometimes you MUST update UEFI.

---

### Post by helen314 on 2020-10-09
Please lay-off the personal  commentaries , it is uncalled for and will be reported to management if it continues .

According to the official doc I need to have 

ONE boot partition on a drive - irregardless of size 

My "boot partition" is mounted as /boot/efi 

MY question is 
should the "type": ( flag in gparted) 
be 
bios-grob 

or 

esp 

It is currently  "esp" 

Could somebody with more knowledge then I please define - in few words
( I can RTFM) 
grub
EFI
UEFI 

**relations .**


And while you at it - describe Ubuntu boot process USING  grub, EFI. UEFI 
describe thie dependencies and PROPER executing sequence - AKA "who is on first?" 

( I will not complicate the question by asking what is grub2 ?  KISS ) 

My ignorance is limited to 
"mounted /boot/efi"  -  as reported by OS during boot 




[LIST]
[*]
[*]
[*]atvrecv - [GPT] This is a flag for Apple TV Recovery Partitions.
[*]bios_grub - [GPT] The partition with this  flag is used as the GRUB BIOS partition. The partition usually uses  about a megabytes of space and is not needed by EFI-booting systems.
[*]boot - [Mac, MS-DOS, GPT, PC98] This flag  indicates that the partition is bootable. On MS-DOS partitioning tables,  only one partition may have this flag. However, other partitioning  tables allow multiple partitions to have this flag.
[*]DIAG - [MS-DOS] The partition is used for recovery and diagnostics.
[*]esp - [MS-DOS, GPT] This flag indicates an  UEFI System Partition.** [COLOR="#FF0000"]GPT uses this flag as an alias for "boot".[/COLOR] **The  UEFI firmware stores files on this partition.
[*]hidden - [MS-DOS, PC98] Partitions with this flag are hidden from Microsoft operating systems.
[*]hp-service - [GPT] This the flag for HP Service Partitions. This partition uses the FAT filesystem.
[*]irst - [MS-DOS, GPT] Intel Rapid Start Technology partitions use this flag.
[*]lba - [MS-DOS] This flag is used by DOS,  Windows 9x, and Windows ME and tells the system to use Linear Mode  (Logical Block Addressing).
[/LIST]

---

### Post by oldfred on 2020-10-09
See also the section at the end of my post linked below in my signature.
Sections at bottom of link:
Links to additional info & what UEFI is
Acronyms

With gpt you have to have either a 1 or 2MB unformatted partition with the bios_grub flag for BIOS boot.
Or an ESP - efi system partition (FAT32) for UEFI boot.

Windows requires a boot flag for BIOS boot on the primary NTFS partition with its boot files.
Grub does not use boot flag, but some older BIOS had to see a boot flag (assumed Windows?)

With UEFI the boot flag and esp flags are often both on the ESP.
Do not confuse the ESP with UEFI boot files for all installed systems and Ubuntu's boot folder or partition. Most desktops do not need a separate /boot partition, but some with servers or server type configurations may want or need a /boot partition (in addition to ESP, if UEFI).
To add to the confusion some systems like systemD-boot also put boot files (kernel, etc) into the ESP.

I started conversions to gpt with my BIOS only system in 2010. All new or repartitioned drives since then have been gpt with either both bios_grub and ESP or now just ESP. I used both when converting from old BIOS system to newer UEFI system as I was not sure where I might want to move drive.

The only reason to use MBR(msdos) partitioning is if you really want Windows in old BIOS mode. A few do prefer that as they understand it. But Microsoft has required vendors to install Windows in UEFI mode to gpt partitioned drives since Windows 8 released in 2012, so only very old systems are now BIOS only.
Ubuntu has not not required gpt partitioning for UEFI installs, but should. I have seen a few posts with newer errors related to MBR and UEFI installs, so maybe Ubuntu has started requiring gpt for UEFI?

---

### Post by dragonfly41 on 2020-10-10
@helen314 wrote above ..

> [COLOR=#000000]Could somebody with more knowledge then I please define - in few words[/COLOR]
[COLOR=#000000]( I can RTFM)[/COLOR]
[COLOR=#000000]grub[/COLOR]
[COLOR=#000000]EFI[/COLOR]
[COLOR=#000000]UEFI[/COLOR][COLOR=#000000]

[/COLOR]I suggest jumping out of the mainstream discussion to read some articles by Rod Smith.

[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

I have installed rEFInd which works alongside existing stuff.
It installs easily enough inside /boot/efi/EFI/
and this is the GUI I now use.


[P.S.]

To answer your other question

> [COLOR=#000000]MY question is[/COLOR]
[COLOR=#000000]should the "type": ( flag in gparted)[/COLOR]
[COLOR=#000000]be[/COLOR]
[COLOR=#000000]bios-grob[/COLOR]

[COLOR=#000000]or[/COLOR]

[COLOR=#000000]esp[/COLOR][COLOR=#000000]

I give below a screenshot of my ESP on my currently running Ubuntu 20.04 external USB 3.0 SSD as seen in Gparted.[/COLOR]

[COLOR=#000000]My Windows 10 stuff is in /dev/sda and I have another Ubuntu in /dev/sdb.

I create a separate ESP for each drive/SSD I use. 
Each ESP contains grub (and rEFInd with its own GUI theme).


[/COLOR]

---

