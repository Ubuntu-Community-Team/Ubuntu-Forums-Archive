---
title: "New Install - Very slow at &quot;Reading package lists...&quot; in apt-get"
date: 2013-01-14
forum: General Help
---

### Post by thisismyusername4now on 2013-01-14
I was running Ubuntu 12.10 on an older computer but on Friday I gathered a stack of new equipment and excitedly assembled a fresh new machine. 

The new machine has Intel i7, 32 GB ram, and a Samsung SSD (Pro 840). This should be a speedy machine.

The Ubuntu install was very slow (took 6 hours, most of that was spent transferring from the CD to the SDD).

After rebooting I noticed that performance was not great, so I went through the standard SSD tweaks and now I get very high numbers for both read and write. 

Performance is great except for one occasion, "apt-get update", or software center.

I develop code under contract using this computer, so I primarily use the command line. However when I execute the update command "apt-get update" it has a performance issue.

After downloading all the files it gets to the section of "Reading package lists..." and takes several minutes. I wrote this post and it is still going. I would estimate that it is more than 10 minutes. My old AMD Athon computer did this same process in seconds. Something is wrong.

Anyone else ever experience a similar problem?

---

### Post by another1LinuxUser on 2013-01-14
Have the same problem. It might not be that slow as you described it, but everytime using apt "reading package lists ... " takes about a minute or more. The installation also took quite long (longer than I experienced so far).

My machine looks like this:
intel i7, 24 Gig RAM and 2 SSDs - one for  / and one for  /home. (Corsair CSSD-F60GB2).

I installed the 12.10 several day's ago. With 12.04 I did not have had this problem.


By the way, what did you do, to speed up your system - regarding the SSD's?

br

---

### Post by SlugSlug on 2013-01-14
6 hours to install is crazy! What internet speed you got as am hoping its awful and the 6 hours was due to pulling in updates.

Not sure if this is the issue you face but try hash our all the deb-src entries in

```
gksudo gedit /etc/apt/sources.list
```

eg 

```
# deb-src http://archive.canonical.com/ubuntu precise partner
```

---

### Post by oldfred on 2013-01-14
My system is a 6 year old dual core with 4GB of RAM. It took about 9 minutes to install to my new SSD a year ago and new clean installs take about the same amount of time. I do install from ISO on hard drive to SSD.

My Internet is fairly fast but it does take 10 to 20 minutes to download updates depending on how old ISO is to current and most of my configuration is now scripted so I have a full working install in about an hour. 
But even on my old laptop with hard drive from flash drive installed in 20 to 30 minutes.

Something is really wrong if it is taking that much time.

Is system in BIOS or UEFI mode? IF BIOS do you have AHCI on?

Have you partitioned in advance or just used auto install?

Is UEFI/BIOS up to date and SSDs version?

       [https://wiki.archlinux.org/index.php/SSD_Benchmarking](https://wiki.archlinux.org/index.php/SSD_Benchmarking)
    
New SSDs have twice the speed as my low cost year old one.

       SSD speed
fred@fred-Precise:~$ sudo hdparm -t /dev/sdd4
/dev/sdd4:
 Timing buffered disk reads: 626 MB in  3.01 seconds = 208.20 MB/sec
Older 160GB rotating drive:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec

---

### Post by thisismyusername4now on 2013-01-14
> **another1LinuxUser said:**
> 
By the way, what did you do, to speed up your system - regarding the SSD's?


Here are the instructions that I used to optimize Ubuntu for the SSD

[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

Sorry that yours is running slow, though I wish mine was done in a few minutes :)

---

### Post by thisismyusername4now on 2013-01-14
> **SlugSlug said:**
> 6 hours to install is crazy! What internet speed you got as am hoping its awful and the 6 hours was due to pulling in updates.

Not sure if this is the issue you face but try hash our all the deb-src entries in

```
gksudo gedit /etc/apt/sources.list
```

eg 

```
# deb-src http://archive.canonical.com/ubuntu precise partner
```

Thank-you for the suggestion, but I do not think it has to do with the internet speed. I am on a 10 mbps connection and the download portion of any Ubuntu updates is very fast. It seems to have something to do with the local machine.

---

### Post by thisismyusername4now on 2013-01-14
> **oldfred said:**
> My system is a 6 year old dual core with 4GB of RAM. It took about 9 minutes to install to my new SSD a year ago and new clean installs take about the same amount of time. I do install from ISO on hard drive to SSD.

My Internet is fairly fast but it does take 10 to 20 minutes to download updates depending on how old ISO is to current and most of my configuration is now scripted so I have a full working install in about an hour. 
But even on my old laptop with hard drive from flash drive installed in 20 to 30 minutes.

Something is really wrong if it is taking that much time.

Is system in BIOS or UEFI mode? IF BIOS do you have AHCI on?

Have you partitioned in advance or just used auto install?

Is UEFI/BIOS up to date and SSDs version?

       [https://wiki.archlinux.org/index.php/SSD_Benchmarking](https://wiki.archlinux.org/index.php/SSD_Benchmarking)
    
New SSDs have twice the speed as my low cost year old one.

       SSD speed
fred@fred-Precise:~$ sudo hdparm -t /dev/sdd4
/dev/sdd4:
 Timing buffered disk reads: 626 MB in  3.01 seconds = 208.20 MB/sec
Older 160GB rotating drive:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec

I started the install at 1:30 pm Saturday afternoon and walked away at 2:00. I came back every half hour or so to check on it... but it really took until 6:00 pm to finish. I guess that is not quite 6 hours, but it took a long time. I was so excited to see the performance of the new hardware.... this was not fun.

I partitioned in advance. SSD is '/' and a 1TB platter is '/home/'.

Good call on the BIOS revision. I checked and I am using a Gigabyte GA-P75-D3 and it has revision 3 of the BIOS. The current stable revision is 9 (beta is 10). I will try to install revision 9 now. 

As for the SSD, is there a way to check the firmware revision from Linux?

Originally I had the system setup with IDE mode (BIOS came that way by default, but I switched it to AHCI which did not help.

Here is what I got from hdparam:
sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads: 656 MB in  3.38 seconds = 194.06 MB/sec

ran it a second time:
sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads:  64 MB in  3.04 seconds =  21.04 MB/sec

That does not bode well....

---

### Post by oldfred on 2013-01-15
Trim does not work unless you have AHCI on. 

New partition tools should set partition alignment correctly. All partitions starts should be divisible by 8. First partition start should be sector 2048. 

You may need to clean up SSD.

I did not correctly enable trim with first install, so I ran this:
       fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by Frogs Hair on 2013-01-15
For the update issue you may want to change download server in update manager settings. If the operating system and download server are the same as the old AMD computer the problem may be elsewhere.

Use software sources to change the sever so you don't have to wait for the update manager to finish before entering settings.

---

### Post by thisismyusername4now on 2013-01-16
> **oldfred said:**
> Trim does not work unless you have AHCI on. 

New partition tools should set partition alignment correctly. All partitions starts should be divisible by 8. First partition start should be sector 2048. 

You may need to clean up SSD.

I did not correctly enable trim with first install, so I ran this:
       fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)


1. I updated the BIOS and it did not help with performance. 

2. I do have the BIOS set to AHCI (was not during Ubuntu install)

Thank-you for the links and suggestions. Here is what I found:

$ sudo fstrim -v /
/: 121008021504 bytes were trimmed


$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       Samsung SSD 840 PRO Series              
	Serial Number:      S12PNEACB11500H     
	Firmware Revision:  DXM03B0Q
	Media Serial Num:   00000000000000000000
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Used: unknown (minor revision code 0x0039) 
	Supported: 9 8 7 6 5 
	Likely used: 9
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  250069680
	LBA48  user addressable sectors:  250069680
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      122104 MBytes
	device size with M = 1000*1000:      128035 MBytes (128 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	    	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	   *	unknown 76[15]
	   *	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	    	Asynchronous notification (eg. media change)
	   *	Software settings preservation
	    	unknown 78[8]
	   *	SMART Command Transport (SCT) feature set
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	   *	SET MAX SETPASSWORD/UNLOCK DMA commands
	   *	WRITE BUFFER DMA command
	   *	READ BUFFER DMA command
	   *	Data Set Management TRIM supported (limit 8 blocks)
	   *	Deterministic read ZEROs after TRIM
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 500253855003dca4
	NAA		: 5
	IEEE OUI	: 002538
	Unique ID	: 55003dca4
Checksum: correct



I am going to try to boot windows and see if the performance improves. Perhaps my drive is faulty.

---

### Post by thisismyusername4now on 2013-01-18
It appears that Linux or the motherboard is the problem. I just finished cloning the partition to a new drive (160 GB SATA 1 platter drive) and after repairing GRUB booted Linux. The apt-get update takes just as long as previously.

What would cause this kind of behaviour?

---

### Post by thisismyusername4now on 2013-01-18
I followed the suggestion I found here:

[http://forum.parallels.com/showthread.php?t=263981](http://forum.parallels.com/showthread.php?t=263981)

But that did not help

I am running out of ideas, any suggestions welcome (short of format and run windows)

---

### Post by thisismyusername4now on 2013-01-19
This is turning into a messy problem. I have tried read/write to other drives, and the same very slow performance happens. 

I am going to repartition my SSD and install windows. See if it suffers from the same performance woes.

---

### Post by oldfred on 2013-01-19
See the comments here about the setting you show as frozen. I do not think that is what your want. May be another BIOS setting.

[http://mackonsti.wordpress.com/2011/11/22/ssd-secure-erase-ata-command/](http://mackonsti.wordpress.com/2011/11/22/ssd-secure-erase-ata-command/)

---

### Post by thisismyusername4now on 2013-01-19
> **oldfred said:**
> See the comments here about the setting you show as frozen. I do not think that is what your want. May be another BIOS setting.

[http://mackonsti.wordpress.com/2011/11/22/ssd-secure-erase-ata-command/](http://mackonsti.wordpress.com/2011/11/22/ssd-secure-erase-ata-command/)


Cool suggestion, but it did not help. I tried the method of putting the computer to sleep and waking it up. The drive is no longer in a frozen state, but the speed has not changed. 

2nd Update: I installed windows and ran a drive speed test. Through any test I ran the drive seemed to run at a very good speed. Attached is the results of an actual test.

---

### Post by thisismyusername4now on 2013-01-21
Bump - Does anyone have this same motherboard (P75-D3)? I am very interested to find someone else who has this board and has success running linux.

---

### Post by daverich on 2013-01-26
I'm having this very same problem. Not just in ubuntu, but with linux mint too (which i guess is ubuntu)

There's definitely something quirky going on here. I had a brand new SSD and it's slow as a tortoise....

Ubuntu boots in seconds however and I love the silence, but for anything else, especially installing stuff, geez- put the kettle on we may be sometime!

Would love to see a fix for this.

---

### Post by thisismyusername4now on 2013-01-27
> **daverich said:**
> I'm having this very same problem. Not just in ubuntu, but with linux mint too (which i guess is ubuntu)

There's definitely something quirky going on here. I had a brand new SSD and it's slow as a tortoise....

Ubuntu boots in seconds however and I love the silence, but for anything else, especially installing stuff, geez- put the kettle on we may be sometime!

Would love to see a fix for this.

Yikes. I have reached the point of deciding it is either the motherboard or the kernel. What motherboard is in your computer?

---

### Post by oldfred on 2013-01-27
What motherboard is it. 

It could be many BIOS setting that may not seem to apply.

Some examples that others posted for older systems. Most will not apply but you can review list:
       Some issues on booting install:
fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.
Though my drive was appearing in the bios and working for install it was actually "disabled"! 
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size or very large / partition over 100GB
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply
Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!
lib64 folder missing??

---

### Post by Buggin on 2013-02-10
I also have this same problem regarding "Reading package lists:" all of the sudden taking a very long time. I also have a SSD but it has nothing to do with the SSD performance. It boots in seconds, sometimes I don't even see the boot screen. It's a dual boot and Win 7 runs through it's boot screen once every time. Exactly once, no longer no shorter (unless it has to do updates). So the SSD is fine. I only have slowness with software center and apt-get update when it comes time to read the package lists. It's 11.9 Mb of data, it can't take very long to read off of anything. Several minutes is crazy. My 11 year old machine did the same thing, like he said, in seconds instead of minutes. It was not like this when I installed. This is new. I do not get any errors. I've tried changing servers. I've removed all but the standard Ubuntu repos. I've cleaned and cleared and deleted lists, ran dpkg commands I found in other posts. I'd say I've done a couple hours worth of different things trying to fix it and nothing has made a bit of difference to apt-get update. I can actually get the Software Center to open now without having to stare at a grey screen for 10 minutes. I have no clue what actually fixed that because it was not my focus. I only noticed it when I opened software center and it actually worked.  Before that, when run from command line, it would hang up at "softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True". I don't know how I fixed one's ability to read the database and not the other's. I have run every command I can find to clear out old caches. As far as I can tell apt-get update package lists are contained in /var/lib/apt/lists only and don't come from anywhere else. I've deleted them and deleted them over and over again followed by different commands. No broken dependencies, no errors of any kind. Just extremely slow performing a relatively simple task. 
Thoughts?

---

### Post by thisismyusername4now on 2013-02-12
It is interesting that other have found similar behaviour. I am assuming that you are running 12.10, what motherboard ar you using?

I have a Gigabyte P75-D3

Here is the bug I created for this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1107150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1107150)


> **Buggin said:**
> I also have this same problem regarding "Reading package lists:" all of the sudden taking a very long time. I also have a SSD but it has nothing to do with the SSD performance. It boots in seconds, sometimes I don't even see the boot screen. It's a dual boot and Win 7 runs through it's boot screen once every time. Exactly once, no longer no shorter (unless it has to do updates). So the SSD is fine. I only have slowness with software center and apt-get update when it comes time to read the package lists. It's 11.9 Mb of data, it can't take very long to read off of anything. Several minutes is crazy. My 11 year old machine did the same thing, like he said, in seconds instead of minutes. It was not like this when I installed. This is new. I do not get any errors. I've tried changing servers. I've removed all but the standard Ubuntu repos. I've cleaned and cleared and deleted lists, ran dpkg commands I found in other posts. I'd say I've done a couple hours worth of different things trying to fix it and nothing has made a bit of difference to apt-get update. I can actually get the Software Center to open now without having to stare at a grey screen for 10 minutes. I have no clue what actually fixed that because it was not my focus. I only noticed it when I opened software center and it actually worked.  Before that, when run from command line, it would hang up at "softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True". I don't know how I fixed one's ability to read the database and not the other's. I have run every command I can find to clear out old caches. As far as I can tell apt-get update package lists are contained in /var/lib/apt/lists only and don't come from anywhere else. I've deleted them and deleted them over and over again followed by different commands. No broken dependencies, no errors of any kind. Just extremely slow performing a relatively simple task. 
Thoughts?

---

### Post by Buggin on 2013-02-12
Umm... not sure what motherboard really. It is a Dell Optiplex 7010. So I guess it's a V8WGR according to my googlefoo. I'm running a new install of 12.10. I installed it probably around 12.10 and did not have the problem. Unfortunately, I'm not really sure when exactly it started. I do recall now that Software Center took forever to open a while back but I ignored it. I haven't really needed to install many packages since I installed. I've been using Ubuntu for a long time so I pretty much already knew what I needed. But occasionally I do still hit the CLI every so often and recently I noticed it, and I got an update for software center so I thought maybe it was a bug and it's fixed, but it didn't go away. Then I found this.

---

### Post by Buggin on 2013-02-13
Just checked and my motherboard has a intel Q77 Express chipset.

I didn't have the install issues you did but then I think I probably installed sooner and wasn't having any issues at all then.

---

### Post by Buggin on 2013-02-15
jhite@optiplex:~$ time sudo apt-get update
[sudo] password for jhite: 
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal InRelease
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates InRelease
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports InRelease
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security InRelease
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal Release.gpg
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates Release.gpg
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports Release.gpg
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security Release.gpg
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal Release
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates Release
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports Release
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security Release
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal/main i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal/restricted i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal/universe i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal/multiverse i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal/main Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal/multiverse Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal/restricted Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal/universe Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/main i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/restricted i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/universe i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/multiverse i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/main Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/multiverse Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/restricted Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/universe Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/main i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/restricted i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/universe i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/multiverse i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/main Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/multiverse Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/restricted Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/universe Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/main i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/restricted i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/universe i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/multiverse i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/main Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/multiverse Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/restricted Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/universe Translation-en
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal/main Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal/multiverse Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal/restricted Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal/universe Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/main Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/multiverse Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/restricted Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-updates/universe Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/main Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/multiverse Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/restricted Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-backports/universe Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/main Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/multiverse Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/restricted Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) quantal-security/universe Translation-en_US
Reading package lists... Done

real	6m16.221s
user	0m3.856s
sys	0m1.284s

It took over 6 minutes to run apt-get update. Over 99% of that time was spent reading package lists.

---

### Post by Buggin on 2013-02-15
This is my formal application for the annual "Derp!" awards.
My problem is solved. I have /tmp mounted in ram. A while back I was messing with something and commented that out in fstab. I forgot I had done that. I noticed when Firefox started getting VERY slow after quite a bit of uptime and use. Then I remembered I had Firefox set to use /tmp and thought maybe I've got RAM going bad. Then I looked and saw that it was commented out so I removed the comment and rebooted and viola. EVERYTHING was fixed. apt-get update, firefox, software center. All working fine now. Probably some other programs that will be screaming along now too. 
So I don't know how many entries we have for the "Derp!" awards this year but throw my name in the hat cause I'm a dummy.

EDIT: Even still I don't understand why commenting out the tmpfs /tmp made a difference. The majority of people don't mount /tmp in RAM anyway. It's certainly not the default setting. So I don't understand why it made a difference if it was a folder under / on the SSD instead of in RAM. Well, I understand there would be a difference, but not a 6 minute difference. My /home is a HDD if that makes a difference. Which it shouldn't.

---

### Post by oldfred on 2013-02-15
Thanks for update. 

I have seen a lot of suggestions of mounting /tmp and other temp files in RAM with an SSD. I only have 4GB have have never done that as I do not want RAM to be used for temp files. 
I have seen temp get used a lot when creating a DVD for example and that would be 4GB. So then I think it would use swap and be slow again?

---

### Post by Joao Lacerda on 2013-02-15
I am doing installations of ubuntu now only from USB, for me it is much faster, and I do not have the risk of damage CD. Maybe it can be something with the cd. 
Good luck

---

### Post by Buggin on 2013-02-15
> **oldfred said:**
> Thanks for update. 

I have seen a lot of suggestions of mounting /tmp and other temp files in RAM with an SSD. I only have 4GB have have never done that as I do not want RAM to be used for temp files. 
I have seen temp get used a lot when creating a DVD for example and that would be 4GB. So then I think it would use swap and be slow again?

Well I have enough RAM to cover a DVD... double layer even. But yes, if you filled your RAM then it would have to go to swap and it would be slower. I've got 14GB and haven't used more than half of it at a time yet and if I ever did I'd probably order more. Actually, I've been trying to find more things to put in RAM. I rarely reboot (uptime *****) so the more stuff I can keep in RAM the better. Obviously, nothing volitile should go in there. Anything you wouldn't blindly delete without a second thought should not be there.

---

### Post by oldfred on 2013-02-15
You will never use swap.

Ubuntu leaves recent activity in RAM as you may go back and reuse it. And only when all the RAM is full will it release the RAM it is caching that is not used. 

So you may see RAM filling up, but only active use matters. And with the amount of RAM you have, you may need to load every program and edit videos to fill it.

To see use:
free -m

---

### Post by Buggin on 2013-02-16
Actually I do use this machine for editing videos, and on the fly transcoding as a DLNA server, and for daily use, all at the same time sometimes. Maybe if I burned a DVD at the same time I could use it all. The one time I did see it get to half useage 3.5 GB was locked up for a virtualbox VM. 
As you can see, the machine is no slouch, which is why I got so worried when it took over 6 minutes to read 12Mb worth of files. Still makes no sense to me really. Most people don't have /tmp mounted in RAM so why when I comment out the mount did it slow down so much performing that task. It's got me quite curious.I guess once /tmp goes RAM it never wants to go back.

---

### Post by jazzgossen on 2013-02-22
Thanks for the updat.e

I have the same problem and a similar setup (root mounted on SSD, /home and /var mounted on HDD, and /tmp mounted on RAM). I do have /tmp mounted as tmpfs, and it isn't commented, and I can confirm when running "mount" that /tmp is indeed mounted as tmpfs, and not on the SSD.

However, every now and then (but not always), "Reading package lists" will take several minutes. I notice the same kind of behaviour also sometimes when saving the machine state of my VirtualBox Windows machine. Sometimes it takes well over 5 minutes. However, restoring it always goes within a few seconds.

Any other idea? (Or maybe I should start a new thread for this.)

---

### Post by AvengerX9 on 2013-04-11
I got this problem too. Dont have any SSD though, but I'm on a quad core pentium with 8gb of ram. Whatever I do it takes ages. Like an hour to install mysql from the command line. Did apt-get upgrade like 15 minutes ago and its still there reading packages and unpacking. In my signature you can see my latest speed test

---

### Post by oldfred on 2013-04-11
It is a bit strange your upload speed is faster than download. But your download speed is faster than mine and my downloads are pretty quick.

Are you connecting to a local mirror? The choose best server is based on ping, not downloads, so sometimes you have to experiment.
On update manager, lower left corner settings button, Ubuntu Software tab, download from combo box, choose other, then select best server.

You can also use top to see if some task is consumming system resources. I keep a tiny processor system monitor in my top panel. (I use gnome-fallback or gnome-panel, so I can add that to top panel.) Or just look at System Monitor to see what does not look correct.

---

### Post by AvengerX9 on 2013-04-11
I dont know what happend. Installing over again, but have run into another problem with the boot loader at the last step of the installation now. My thread is here [http://ubuntuforums.org/showthread.php?t=2134098&page=4&p=12598955#post12598955](http://ubuntuforums.org/showthread.php?t=2134098&page=4&p=12598955#post12598955)

---

### Post by javaguru on 2013-10-09
I have the exact same problem, only it's not only apt. Chrome is "waiting for cache" a lot, other simple operations take forever, and **iotop** reports very high I/O usage  - around 99,5%. Has anyone found anything out ?

---

### Post by Logics on 2013-12-10
I installed 12.04.4 32-bit and, at first, [sudo apt-get update] went pretty fast everytime. I installed a few items I knew I needed for my particular situation, (PAM modules, etc), and "Reading package lists..." was quick as expected.
after doing [sudo apt-get upgrade], that is when [sudo apt-get update] started taking about 1 hour for "Reading package lists...".

Now root (/) and boot (/boot) are on my SSD (sdb). My HDD, (sda), has /home, /tmp, /var/tmp, /var/log & /var/spool to reduce writes to the SSD.

So the problem does not exist on first boot/install but does exist after first upgrade.

System is an HP Z820 dual Xeon. Also seen on HP Z220, ASUS Sabertooth and HP Compaq Elite 8300. Seen on HDDs and SSDs. Seen with AMD and nVidia GPUs. Seen before my PAM module installs and after my PAM module installs (that is why I now do my app installs first and my upgrades after). Seen on Core i7s and on Xeons.

Yes, I did say about 1 hour! Just for  "Reading package lists...".

Downloads of all packages happen in matter of seconds! It is not Internet speed which is [http://www.speedtest.net/my-result/3156565400](http://www.speedtest.net/my-result/3156565400)

UPDATE: For the record, as it was mentioned in another thread, when all of /var was mounted on the SSD, I still had the same issues. Also, SSD is an HP branded Micron RealSSD(tm) C400 128GB SATA 6Gb/s.
For clarity, issue still exists without SSD installed and system loaded on HDD only. It is not an SSD issue.

cached reads: 7,000+ MB/s, buffered disk reads: 180+ MB/s

---

### Post by oldfred on 2013-12-10
Years ago when Ubuntu needed 256MB to install I installed to a old laptop with only 128. I think it only worked because I already had swap, but since it was using swap so much it took about 6 hours to install and 8+ (all night) to download and install updates. Systems worked but was so slow as to not be usable. Lighter weight install then did work. So too little RAM can cause those kind of issues.  Is RAM shown correctly?

Also using 32 bit operating system on 64 bit hardware does slow system down, but not that much.

---

### Post by Logics on 2013-12-12
Most of my systems have 32 GiB RAM and swap. Some have only 16 GiB each. Ubuntu does show the correct RAM amount.

I do understand a little slow down with 32-bit OS on 64-bit HW but my single 2.4GHz PhenomII six-core with 8GiB RAM and swap Mint 14 64-bit installed on a platter, out performs the dual 3.6GHz Xeon quad (eight real cores total, 16 if you actually count hyperthreading) core with 32GiB RAM and swap Precise 32-bit installed on an SSD. This "out-perform" only really comes regarding "sudo apt-get update", boot time and shutdown time. (plus a few other tasks).

Outside of that, the system is really fast.

---

### Post by oldfred on 2013-12-12
If you installed 32 bit Ubuntu on a 32GB RAM system, you are not using RAM well. While PAE does allow over the 3GB limit of 32 bit installs, it does not use it all at once. It has to swap each app in and out. 

 Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

 Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)

Do not know about downloads, but for booting you can look at dmesg and see if there are long delays posted, error messages or just drivers that keep trying and then either fail or succeed. 
The 12.04 has a log file viewer.
Or 
gksudo gedit /var/log/dmesg


There are many other log files that may give clues to other issues.

---

### Post by virgil2 on 2014-02-25
Looks like a lot of people (including me) are having this problem.  
System:  asus essentio cm1730
amd x6, 16Gb ram, 2 1Tb HDD set as a volume group.  
Last internet speed test - 70Mbps.   Running new install of 13.10
Install only took a little less than an hour.  Downloaded all updates during install.  Trying to get 32 bit libs for playonlinux has taken days (still not finding what I need.)  Have had to add repos and run atp-get update a lot.  So, I am burning through my copied episodes or Star Trek and Stargate waiting.  Not sure what other info I should add here.  Trying to dump windows and go totally linux.  I do like to play diablo 3, Civ4, and SC2, which is the only reason I kept win7 for so long

---

### Post by Noki0100 on 2014-02-28
Hi, I had this same issue, for me switching to 64 bit version fixed the problem. Which to me suggests that all of my settings are correct and it is something within Ubuntu that causes the problem. I also get the same issue in Mint but not Debian. So this suggests that a change to Ubuntu which isn't in Debian is causing these problems.

---

### Post by superian on 2014-03-17
Ah, it's not just me :)

I am getting exactly the same issue as many others here - after a long time of working perfectly, the 'reading package lists' part of doing an apt-get update has become *extremely* slow. Using time on two runs shows..

> (assorted getting repository data lines which appear at normal speed deleted)
Reading package lists... Done

real    28m27.642s
user    0m19.944s
sys    0m7.828s

> Reading package lists... Done

real    33m20.122s
user    0m25.228s
sys    0m11.808s

.. for example. It feels longer :)

I am almost tempted to keep running this to see if the time ever gets shorter, but the difference may just reflect the browsing etc that I am doing while waiting for it to finish.

I am using an SSD drive for /, it is trimmed, it is still quick for everything else I can notice... and it didn't used to be like this. This installation is about four months old.

It is an AMD-based PC, not an Intel one. It's also an i386 installation rather than an x64 one - I can see that switching to the other one may speed things up in the short term, but I wonder if the problem will reappear in a few months.

---

### Post by beckch on 2014-03-23
I installed VirtualBox 4.3.8 yesterday on a i7 with 8Gb Ram running Win7. Then proceded to install a 12.04 ubuntu server as a VM. I went with all the defaults except changed disk image to qcow2 so I can transfer to one of my servers at some point.
Install was pitiful...it took over 12 hours and then crashed on first apt-get update. - write errors

Slow VMs seem to be a common problem when using Virtual Box and in this case I suspect I missed something in my haste accepting defaults. My problem I guess is something like using dynamic disk allocation because my 20Gb VM is residing in a 1.5Gb disk image! Also did I miss an option for VirtIO instead of SATA? 

My question is can I fix this or should I start again?

Also can anyone give me a quick rundown of how to get my trackpad to scroll the VM window?

---

### Post by superian on 2014-06-19
> **superian said:**
> Ah, it's not just me :)

I am getting exactly the same issue as many others here - after a long time of working perfectly, the 'reading package lists' part of doing an apt-get update has become *extremely* slow. 

..

I wonder if the problem will reappear in a few months.

A shutdown and restart got it back to normal back then, but yes, the problem has reappeared.

/ is still on an SSD (/dev/sdb) which should be (is) noticeably faster than the spinning rust drive (/dev/sda):

/dev/sdb1:
 Timing buffered disk reads: 622 MB in  3.00 seconds = 207.09 MB/sec


/dev/sda7:
 Timing buffered disk reads: 238 MB in  3.00 seconds =  79.20 MB/sec

.. but this one thing has become appallingly slow again.

Time to reboot.

---

### Post by superian on 2014-06-19
Hmm, reboot has solved this again, but what was the problem?

---

### Post by mattias5 on 2014-08-31
Hi,

i had the same problem as other in this thread , corei7 , 32GB ram and intel 120Gb ssd and did an upgrade to 14.04 32bit, and my system went SLOOOOOW.
But in rescue mode the system whas fast again, after some hours with google i found this post "https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-trusty/+bug/1333294" and added the "mem=8000m" to my kernel options i grub and the system was fast again.
This post says that the problem starts when ram is more than 18GB, not tried this yet.

This post also have some tips around the problem, "https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1264707/comments/18"

//Mattias

---

### Post by gacb on 2015-03-08
I don't have an answer, but I'm running three flavours of Ubuntu; Unity, Gnome and Mate. The Unity one is slow at reading the package list but there's no problem with the other two.

My disk activity light also runs continually for at least 10 minutes while the others don't. A third clue is that fsck runs every time I boot Unity.

 I'm seriously considering reformatting the Unity partition and staring over.

---

### Post by Steven_Stuber on 2015-08-20
> **mattias5 said:**
> Hi,

i had the same problem as other in this thread , corei7 , 32GB ram and intel 120Gb ssd and did an upgrade to 14.04 32bit, and my system went SLOOOOOW.
But in rescue mode the system whas fast again, after some hours with google i found this post "https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-trusty/+bug/1333294" and added the "mem=8000m" to my kernel options i grub and the system was fast again.
This post says that the problem starts when ram is more than 18GB, not tried this yet.

This post also have some tips around the problem, "https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1264707/comments/18"

//Mattias

This works!!!!! I have been battling this for 2 days and finally found a solution. I set mine to 8192M.

to edit, do this:

**sudo gedit /etc/default/grub**

find line that says GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"      (yours might have more stuff in here)

and add mem=8192M into the quotes. make sure you leave a space after the last entry (splash in my case)

looks like this
[I]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem=8192M"[/I]

save and close the file

then dont forget to run this in the terminal to update your grub config file:
[B]
sudo update-grub[/B]

Fixed many issues with my linux install on a beast of a machine with 24gb of ram.

---

### Post by cedricstokes on 2016-07-07
> **Steven_Stuber said:**
> 

to edit, do this:
**sudo gedit /etc/default/grub**
find line that says GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"      (yours might have more stuff in here)
and add mem=8192M into the quotes. make sure you leave a space after the last entry (splash in my case)
looks like this
*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem=8192M"*
save and close the file
then dont forget to run this in the terminal to update your grub config file:
**sudo update-grub**

Fixed many issues with my linux install on a beast of a machine with 24gb of ram.

It works for me too.
Thanks a lot !!!

---

