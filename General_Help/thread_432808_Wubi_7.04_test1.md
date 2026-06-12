---
title: "Wubi 7.04 test1"
date: 2007-05-04
forum: General Help
---

### Post by ecology2007 on 2007-05-04
This is for testing purpose only.
What's new ?

> 
Allow kernel upgrades. (experimental)
Supports a wider range of sata and usb devices. (experimental)
Network settings detection. (experimental)
New user interface allowing drive settings, ubuntu edition and language selection. (experimental)
Automatic installation of ntfs-3g and auto - mount of the NTFS host drive.
Warning : 
If you allready have wubi, you need to uninstall it first.
You can backup the iso in wubi/install if you want to avoid downloading it again.
You can uninstall wubi by running the previous wubi.exe or uninstall.exe in wubi folder.

Known issues :
Does not work with Vista.
Does not work with FAT32 drives.
Has issues with raid 0 arrays.

You can get it here (same as minefield 0.4):
[http://cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/Wubi-7.04-test1.exe](http://cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/Wubi-7.04-test1.exe)


Previously :
Minefield 0.3
[http://cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-minefield0.3.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/wubi-7.04-minefield0.3.exe)
Minefield 0.4 is also available (should fix an issue with reboot):
[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.4.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.4.exe)


If you have trouble downloading the iso, get it here, and save it in the same folder as wubi.
[http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso)

If you find any bug or notice anything, post it in this thread.

---

### Post by celsus on 2007-05-04
Please provide a link to a version of the wubi installer which ISN'T a minefield and which behaves as described at the Wiki!

---

### Post by ecology2007 on 2007-05-04
After we have gathered enough feedback on this minefield, there will be a final release. Not before.
The wiki has been updated.

---

### Post by celsus on 2007-05-04
Thanks, I'll read the revisions.  I'm waiting for a fix to error 17 before re-installing.  I had wubi in the root of D: (slave on IDE 0) of a 20GB 5800 RPM IDE HD, along with contig and the Xubuntu .iso the wubi installer ignored.
I had previously used fsutil to create a large file to try to maneuver the wubi installation into completely contiguous space at the end of the partition but this did not work as I expected.  After defragmentation, I had a completely defragmented (but not contiguous) wubi at the beginning of the partition.  On what basis would fragmentation (unless extreme) actually cause failure of loading or other access to the embedded file system?

---

### Post by ecology2007 on 2007-05-04
Fragmentation of either wubi/initrd or wubi/linux in 2 pieces is enough to raise grub error 17. Theses files are less than 10 MB each.
Fragmentation of any other file is unrelated with error 17, but can slow disk readings and writings.
Note that any software dealing with files that are several gigabytes would suffer as well.

---

### Post by ecology2007 on 2007-05-04
The wiki gives you a way to handle multiple wubi install, you do not need that.
If you want to install xubuntu, the best way is
1 . install ubuntu (wubi or not)
2. type in a console :
```
sudo aptitude install xubuntu-desktop
```You will have exactly the same thing as with a xubuntu iso.
if you want kubuntu
```
sudo aptitude install kubuntu-desktop
```

---

### Post by countstex on 2007-05-04
Hi, I ended up here as this release was stated as increasing support for RAID-0 systems, however it appears not to be working in my case. This is using RAID-O of a ASRock 939-Dual-SATAII mobo

---

### Post by ecology2007 on 2007-05-04
Good.
It seems that you passed the grub stage and started the boot. Give us more details about your configuration, check if there is a logfile in wubi/logs and post the content here (but that seems very unlikely to me).

---

### Post by celsus on 2007-05-04
ago supplied [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-desktop-i386.iso](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-desktop-i386.iso)
which I am downloading now -- if I place that and minefield2.exe or minefield3.exe in the root of D: (an uncompressed NTFS volume) and wubi is made contiguous then execute minefield, will I get a bootable Xubuntu installation in D:\wubi?  Note that I had a completely defragmented disk when I got error 17.

---

### Post by countstex on 2007-05-04
> **ecology2007 said:**
> Good.
It seems that you passed the grub stage and started the boot. Give us more details about your configuration, check if there is a logfile in wubi/logs and post the content here (but that seems very unlikely to me).

No logfile, not even gotten as far as creating the folder for them it seems. 

I have the following specs, let me know if there are any other particulars you would like to know:

**OS:** WinXP SP2
**CPU:** AMD 64 3700+
**RAM:** 2 GB
**Mobo:** ASRock 930-DualSATAII
**HDD:** 2xSegate 7200.9 250GB in RAID-0
**RAID:** Onboard ULi SATA/RAID Controller M1689/M1567
**ISO:**ubuntu-7.04-alternate-i386.iso

I got the same errors earlier this evening when I first tried Wubi with minefield2

---

### Post by ecology2007 on 2007-05-04
No.You can install xubuntu with this CD but not using wubi.  It is a live CD version, we are using the alternate one.
Where did ago supply this link ?
The correct one for xubuntu and wubi is :
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso)
It will not solve magically "error 17" issues.

---

### Post by ecology2007 on 2007-05-04
> **countstex said:**
> No logfile, not even gotten as far as creating the folder for them it seems. 

I have the following specs, let me know if there are any other particulars you would like to know:

**OS:** WinXP SP2
**CPU:** AMD 64 3700+
**RAM:** 2 GB
**Mobo:** ASRock 930-DualSATAII
**HDD:** 2xSegate 7200.9 250GB in RAID-0
**RAID:** Onboard ULi SATA/RAID Controller M1689/M1567
**ISO:**ubuntu-7.04-alternate-i386.iso

I got the same errors earlier this evening when I first tried Wubi with minefield2

What i would like to know is some details on your raid and partition setup.
How many partitions do you have, what are their letters inside windows...
From what i guess from your screenshot, wubi is on the first partition of the first drive, it is your bios that makes the RAID stripping. 
Do you see a single drive of 500 Gb under windows, control panel, admin tool, computer, disk management ?
Do you know if it is 100 % hardware raid, a hardware fakeraid ( like the various SATA "raid" controlers that several motherboards come with in the last year ), or windows software raid?

---

### Post by countstex on 2007-05-04
> **ecology2007 said:**
> What i would like to know is some details on your raid and partition setup.
How many partitions do you have, what are their letters inside windows...
From what i guess from your screenshot, wubi is on the first partition of the first drive, it is your bios that makes the RAID stripping. 
Do you see a single drive of 500 Gb under windows, control panel, admin tool, computer, disk management ?
Do you know if it is 100 % hardware raid, a hardware fakeraid ( like the various SATA "raid" controlers that several motherboards come with in the last year ), or windows software raid?

Single partition of the full 500MB, appears as C: in Windows (Disk 0)
The stripe was setup in the RAID Bios, wanted to keep Windows out of the picture
Can't be sure about the fakeRAID situation, will look into the ASRock site and see what I can dig up.

Update: Found this information confirming is as fakeraid...

AHCI mode  &#8212; fakeraid. Intel's Advanced Host Controller Interface is an open-standard PCI abstract device layer for mass-storage access describing a fairly advanced SATA interface ("HBA" = host bus adapter), in theory supporting native command queuing (NCQ) with per-device queues, hotplug, port multiplexer, etc. It's currently represented by Intel's ICH6-R and ICH6-M chipsets, **ULi's (formerly ALi) M1575 and M1567** 4-port SATA-II PCI Express South Bridges; and some chipsets from SiS, VIA, Nvidia, ATI, and JMicron. libata AHCI driver "ahci" became available starting 2.4.29-preX and 2.6.9-rcX, and is now production quality. If your desired installation kernel lacks "ahci", you may be able to use a pre-AHCI fallback mode (e.g., the ICH5-like fallback mode of Intel ICH6/ICH6-R chipsets): Look in your BIOS Setup program for a "legacy" or "ATA" setting, e.g., as reported by Peter Knaggs for his Dell Dimension XPS Gen 3 Series / Intel 925X Express chipset motherboard.

---

### Post by dbgeezer on 2007-05-05
I just downloaded minefield3 and installed it

I like the new install startup screen.  very professional looking.

However I got the same results as I reported before.

1) On initial reboot, I got "ATA1.0: Set of native returned 0; expected 195371568" after boot (or perhaps 'loading..').

2) On final reboot, no gui.  (screens found but not usable)

3) I might be able to get around this, but I can't get to the network (at home where I only have wireless).  Wireless doesn't work because I have to enter my WEP key.

When will the version that starts the gui with more generic drivers (than my Radeon X1300) come out?

Thanks

---

### Post by ago on 2007-05-05
There is a boot issue with minefield0.3. I uploaded some fixes in bzr. But cannot upload a new build since I have zero bandwidth ATM.

---

### Post by celsus on 2007-05-05
Excuse me, you supplied the link at [http://ubuntuforums.org/showthread.php?t=396546](http://ubuntuforums.org/showthread.php?t=396546):
> **ecology2007 said:**
> There is no final build for ubuntu 7.04 yet. You can safely use this link if you can not wait.
This are the iso we are using, they will remains the same at least for 4 or 5 months :
[Ubuntu] 
[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)
[Kubuntu] 
[http://releases.ubuntu.com/kubuntu/feisty/kubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/kubuntu/feisty/kubuntu-7.04-alternate-i386.iso)
[Xubuntu] 
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso]("http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso")

I have read everything at the Wiki.  You have now referred me back to the same .iso that minefield2.exe failed to recognize when placed in the root of **uncompressed, NTFS** volume D: (together with the .iso), as I indicated in previous posts.  When I executed minefield it proceeded to download ubuntu.  When the installation was finished I **completely** defragmented D: with Diskeeper.  After rebooting the grub loader terminated with error 17.  I used the alternate Xubuntu .iso and followed the procedure described at the Wiki but the result was an unbootable image.

---

### Post by ago on 2007-05-05
celsus, error 17 depends on a program that is not under our control (grub for windows). The compression and fragmentation are common problems, but they are not necessarily the only problems... In that case the best (and only) option is to install wubi on a different partition/HD.

---

### Post by ago on 2007-05-05
I managed to upload minefield 0.4, see first page of this thread. Since I have no windows I could not test it fully

---

### Post by celsus on 2007-05-05
I understand that the grub loader is not your program, but Wubi's volume emulation needs to be invoked by it successfully.  The error suggests to me (with no linux experience) that grub can't access the virtual linux volume at all; I infer that there is a bug in Wubi rather than grub.  You say at the Wiki that D: is OK; perhaps you should revise this to say that D: may be OK.  What is the underlying issue?  It seems to me that an incorrect path might be being passed to grub.

---

### Post by ago on 2007-05-05
What happens is that grub has to load the kernel AND the initrd (a mini filesystem containing other required userspace files to boot). When you see the error 17 in grldr it means that the kernel and/or the initrd cannot be loaded at all. We come into play only once the initrd is loaded (lupin _is_ the initrd), but after that happens it is quite unlikely for you to experience an error 17.

---

### Post by ecology2007 on 2007-05-06
> **countstex said:**
> Single partition of the full 500MB, appears as C: in Windows (Disk 0)
The stripe was setup in the RAID Bios, wanted to keep Windows out of the picture
Can't be sure about the fakeRAID situation, will look into the ASRock site and see what I can dig up.

Update: Found this information confirming is as fakeraid...

AHCI mode  &#8212; fakeraid. Intel's Advanced Host Controller Interface is an open-standard PCI abstract device layer for mass-storage access describing a fairly advanced SATA interface ("HBA" = host bus adapter), in theory supporting native command queuing (NCQ) with per-device queues, hotplug, port multiplexer, etc. It's currently represented by Intel's ICH6-R and ICH6-M chipsets, **ULi's (formerly ALi) M1575 and M1567** 4-port SATA-II PCI Express South Bridges; and some chipsets from SiS, VIA, Nvidia, ATI, and JMicron. libata AHCI driver "ahci" became available starting 2.4.29-preX and 2.6.9-rcX, and is now production quality. If your desired installation kernel lacks "ahci", you may be able to use a pre-AHCI fallback mode (e.g., the ICH5-like fallback mode of Intel ICH6/ICH6-R chipsets): Look in your BIOS Setup program for a "legacy" or "ATA" setting, e.g., as reported by Peter Knaggs for his Dell Dimension XPS Gen 3 Series / Intel 925X Express chipset motherboard.

Thanks for the report.
We allready include the kernel modules raid0, ahci, and sata_uli. Most of what is needed for your configuration is there. None of us uses RAID 0 and we can not work further on this issue for now. We may consider using dmraid in the future.

---

### Post by ecology2007 on 2007-05-06
> **dbgeezer said:**
> I just downloaded minefield3 and installed it

I like the new install startup screen.  very professional looking.

However I got the same results as I reported before.

1) On initial reboot, I got "ATA1.0: Set of native returned 0; expected 195371568" after boot (or perhaps 'loading..').

2) On final reboot, no gui.  (screens found but not usable)

3) I might be able to get around this, but I can't get to the network (at home where I only have wireless).  Wireless doesn't work because I have to enter my WEP key.

When will the version that starts the gui with more generic drivers (than my Radeon X1300) come out?

Thanks

Thanks for the report.

1.Some warning messages may occur, you can ignore this one if it does not show up again.

2. wubi is working for you and succesfully installed, you have a confict between xorg and your hardware.
Try to find if are more lucky in general forum.
(search for x1300 and xorg specifics issues, if none search for dpkg reconfigure xorg)
We will never ship more drivers that the ubuntu defaults.

3. It is expected behavior, we can not yet retrieve wep, wpa, wpa2 and other related settings from windows.

---

### Post by celsus on 2007-05-06
OK, I installed again to D:; couldn't boot, moved wubi to C:, and booted successfully into Kubuntu (doesn't seem to handle streaming media or .avis after applying updates -- but I suppose that's irrelevant to wubi problems).  I installed NTFS support from the package manager.  When I opened the file system settings, D: was visible but still could not be mounted.  There is nothing exceptional about it -- an aging Maxtor 20GB IDE with 4KB of bad sectors formatted uncompressed NTFS configured as a slave on IDE 0.  I installed Fluxbuntu to this drive, in this configuration, and was able to dual-boot (by allowing the installation to alter MS' MBR).

---

### Post by dbgeezer on 2007-05-06
> **ecology2007 said:**
> 
2. wubi is working for you and succesfully installed, you have a confict between xorg and your hardware.
Try to find if are more lucky in general forum.
(search for x1300 and xorg specifics issues, if none search for dpkg reconfigure xorg)
We will never ship more drivers that the ubuntu defaults.

Thanks,  I'll check the boards. I thought that i saw a note from you (or one of the other developers) that a more generic xorg would be included.  Perhaps whoever, was referring to the ubuntu folks.  At any rate, I thought that this problem was supposed to be ironed out by delivery of feisty. 

> **ecology2007 said:**
> 3. It is expected behavior, we can not yet retrieve wep, wpa, wpa2 and other related settings from windows.

I'll research this a bit.  It should be possible to get those out of windows.

---

### Post by Spegelius on 2007-05-08
> **ecology2007 said:**
> Thanks for the report.
We allready include the kernel modules raid0, ahci, and sata_uli. Most of what is needed for your configuration is there. None of us uses RAID 0 and we can not work further on this issue for now. We may consider using dmraid in the future.

I've been trying to get ULi RAID working (some posts  in here: [http://ubuntuforums.org/showthread.php?t=396908&page=9](http://ubuntuforums.org/showthread.php?t=396908&page=9) ). It seems that it's not possible at the moment. dmraid doesn't support ULi. Kernels default sata_uli.ko doesn't support RAID and the driver ULi provides doesn't support Ubuntu (incompatible module format). And ULi was bought by nVidia, so i think driver development might be stopped...

However, i got some progress about software RAID and lupin; i installed mdadm, which detected my Windows software RAID automatically. After that i manually added modules md_mod amd dm_mod to lupin source file (modules) and built lupin. Using the built kernel and initrd, my RAID setup was automatically detected during booting, as i understand, BEFORE lupin mounted the disk images and started normal boot process. I haven't tested more than that. To verify, could try to get the /dev/md1 device mounted by lupin and try to boot from disk images copied to the RAID set.

My view of getting RAID to work with lupin; you need either a driver supporting RAID for the chipset in question OR you need to use dmraid (which works even when the driver doesn't know anything about RAID). I think mdadm doesn't support RAID sets generated by fakeraid chipsets, only some software RAID setups.

---

### Post by ago on 2007-05-08
Spegelius, none of us uses raid. So if you have a working patch that does not increase size too much, feel free to send it over. Or apply to the the lupin-team so that you will be able to commit that. This is for you: [https://bugs.launchpad.net/lupin/+bug/113280](https://bugs.launchpad.net/lupin/+bug/113280) ;)

---

### Post by Spegelius on 2007-05-09
No working patch yet, but some observations:

- M$ dynamic disk RAID, mdadm and ntfs-3g. Seems no-go at the moment. I can get the RAID set created in Windows to work read-only when mounting it with kernel ntfs support. However, ntfs-3g complains about not being able to read last sector and doesn't mount it. Author of ntfs-3g says that the volume is somehow dirty, as it won't mount. It's unclear if it's about mdadm, ldm support (or way ldm volumes are handled generally) or ntfs-3g.
Result: one can't have a fully working software RAID (usable in both Windows and Linux) as a host for Wubi. However, if mounting the RAID set with kernel ntfs support, in rw mode, one should be able to use the RAID disk as home for Wubi (as the disk images are fixed size).

- fakeraid chipsets and dmraid: i have Intel chipset on my server and i'm planning to test dmraid on it, as it's HDs are in RAID0 (2x400GB). dmraid support intel chipsets, so should be ok.

- mdadm and dmraid related to Wubi: simply by installing dmraid and mdadm, new initrd is generated automatically (and with more recent kernel-update lupin scripts, automatically lupinisized... :) ) containing both dmraid and mdadm. For dmraid, the command 'dmraid -ay' is executed, meaning all detected RAID sets should be assembled. Also some seach scripts for mdadm exist, but for me mdadm seems to default to mdadm.conf (which is included to the initrd automatically ) and no scan is performed. The problem currently is that these SEEM to be executed after lupin scripts during, so disk images can't be scanned (i'll have to check this...). Actually the initrd execution order is unclear to me...

---

### Post by ago on 2007-05-09
Insert pause_for_debug somewhere in lupin code, also put pause_for_debug in menu.lst as a kernel parameter. Now when you but it should pause and give you a shell. Try to execute mdraid commands manually and mount the drive manually. You might have to add mdraid in the binaries file as well to make it available at boot time.

---

### Post by Spegelius on 2007-05-09
Allrigh, some success. Copied Wubi.7.04-test1 contents to my servers C: with empty disk images, booted with kernel and initrd that were generated last time i installed dmraid and mdadm. dmraid and mdadm were active during boot and dmraid actually managed to create the raid devices! However, lupin didn't find host and after 3 mins of waiting, i was greeted with initramfs prompt. Looking at /dev/mapper, three device files were created: isw_jaddajaddablaablaa_RAID, isw_jaddajaddablaablaa_RAID1 and isw_jaddajaddablaablaa_RAID5, latter two being the two partitions i have. Mounting them with ntfs-3g worked flawlessly and copied the zenigdata.log to another of the mounted raid partitions. In the logs it's evident that lupin only tries /dev/sda and /dev/sdb (the two drives my server box has), not the /dev/mapper-files. Is this because lupin looks only in the /dev-folder, not the additional subfolder, mapper? I'll add those debug lines to the code and see if i get any smarter...

---

### Post by Spegelius on 2007-05-09
Ok, installation started. Added /dev/mapper*RAID[0123456789] to the list_devices function as search param and we're rolling :)

---

### Post by ago on 2007-05-09
> **Spegelius said:**
> Is this because lupin looks only in the /dev-folder, not the additional subfolder, mapper? 
Yes. The relevant code that generates the list of devices to search is in 

lupin/src/initramfs/scripts/lupin-functions

243   list_devices(){  
244       ALLDEVICES=  
245       for dev in /dev/[sh]d[abcdef][123456789] /dev/[hs]d[abcdef]; do  
246           if check_fs ${dev}; then  
247               ALLDEVICES="${ALLDEVICES:+$ALLDEVICES }${dev}"  
248           fi  
249       done  
250   }

---

### Post by ago on 2007-05-09
Do mdraid & co need to be installed in the system that compiles lupin? If so you need to modify lupin/scripts/build.sh/prerequisites() and have that install the required files if not available.

---

### Post by Spegelius on 2007-05-09
Yeah, now writing this from fresh from the owen, spanking brand new, RAID 0 installation of Wubi Feisty (I do believe that i'm the first one... ;) ).

For fakeraids to work (nvidia, via, intel etc), dmraid must be installed and yes, it should be added as prerequisite. Ubuntu's dmraid package seems sophisticated enough to automatically add itself to initramfs creation process (scripts and binaries).

For software raids, mdadm goes just like dmraid. Install it (from Ubuntu repos) on build machine and it's on the initramfs build scripts. Add as prereq. However, mdadm has to be studied more to get Windows software raid working, for ntfs-3g doesn't seem to work with it and it's RAID autodetection is unknown...

To recap what i did:
- latest minefield sources from bzr
- added these to modules-file:
    dm_mod
    md_mod
    (dmraid requires also dm_mirror, but it seems that this comes automatically. However, better to add it than be sorry)
- installed dmraid Ubuntu package
- installed mdadm Ubuntu package
- updated list_devices() in lupin-functions to search also /dev/mapper/*RAID[0123456789]
- built and used

I think all those modules i mentioned might be allready defined by dmraid and mdadm, so i'm not sure if those matter... also the search string should be verified that dmraid allways makes devs fitting on that category.

BTW, is there a way to bench disk speed in linux?

---

### Post by ago on 2007-05-09
> **Spegelius said:**
> To recap what i did:
Good job,

Feel free to commit to the devel branch (use bzr diff and bzr status to check that everything is in order before committing, send me a line if you need help with bzr).

> I think all those modules i mentioned might be allready defined by dmraid and mdadm, so i'm not sure if those matter...
Let's keep them anyway (unless there is any strong reason not to).

> also the search string should be verified that dmraid allways makes devs fitting on that category.
Don't understand what you are saying...

> BTW, is there a way to bench disk speed in linux?
There are several benchmarks like bonnie++. It would be interesting to compare wubi performance to an official installation. If you run the tests please let us know. We can publish some chart on the website.

---

### Post by Spegelius on 2007-05-09
> **ago said:**
> Good job,

Feel free to commit to the devel branch (use bzr diff and bzr status to check that everything is in order before committing, send me a line if you need help with bzr).


I'll have a look at committing those changes tomorrow, i've only used bzr for checking out stuff.

> **ago said:**
> 
Let's keep them anyway (unless there is any strong reason not to).


Agreed.

> **ago said:**
> 
Don't understand what you are saying...


What i meant was that i don't know if the dmraid generated dev-files are named allways *RAID[123...]. So the search pattern might need some revising at some point. But i think current is a good starting point.

bonnie++ doesn't seem to work properly, or i did something wrong. After running a while, it says that its doing something intelligently and freezes. Mouse cursor moves, but system doesn't respond. Ran it on both of my Feisty boxes, both did the same thing. Other has been in that state for 20 minutes now, no disk activity or anything.

---

### Post by ecology2007 on 2007-05-09
Great !

---

### Post by Spegelius on 2007-05-10
Ok, figured out bzr and committed the changes to devel brach. I didn't add mdadm just yet, as it's no good anyways...

About the software raid support; yesterday i found out that one way to get r/w support with Windows software raid sets is to use ntfsmount instead of ntfs-3g. I copied some stuff to the RAID0 set and it all worked ok even after booting back to Windows. I didn't do anything fancy (like creating long folders etc). Also ntfsmount authors claim that operations potentially hazardous just refuse to proceed so no corruption should happen. See [http://wiki.linux-ntfs.org/doku.php?id=ntfsmount](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount). Ubuntu kernel doesn't seem to have ntfs RW support enabled and ntfs-config doesn't seem to see the raid device, so ntfsmount should be usable. I was thinking something on the lines of making a special case for all /dev/md* devices, as those are the mdadm generated RAID devices and mounting them with ntfsmount instead of ntfs-3g.

---

### Post by ago on 2007-05-10
> **Spegelius said:**
> Ok, figured out bzr and committed the changes to devel brach. I didn't add mdadm just yet, as it's no good anyways...
Good I updated the bug report

> About the software raid support; yesterday i found out that one way to get r/w support with Windows software raid sets is to use ntfsmount instead of ntfs-3g.
Too dangerous to change that just to support windows softare raid... I doubt there are that many users anyway and if someone can be bothered to setup a software raid then probably he will be able to figure out how to partition the hard disk. I'd say we can safely drop windows software raid support. There are far more important issues such as Vista support, grldr error 17, and progressbar for gigen.

---

### Post by Spegelius on 2007-05-10
You're propably right. And it seems that mdadm's autodetection isn't working currently during boot (it being too risky), so that wouldn't have worked easily anyway. I'll fool around with the code anyway, for my personal use. I'd like to get Wubi disk images dumped to the RAID set for my main pc also.

---

### Post by bobp0303 on 2007-05-30
Got the DVD writer going fine -- installed the system and it works fine except no video after the initial splash screen.  I have an NVIDIA card -- works fine with Feisty Fawn and previous versions.  I thought there might be a problem because I hadn't installed the video portion of the studio, so I reinstalled with everything -- still no video.  Any suggestions?

---

### Post by ago on 2007-05-30
> **bobp0303 said:**
> Question: -- before I trash my system at home:)
Will Wubi work to install the Ubuntu Studio ISO?  The reason I ask is that US is a DVD ISO and doesn't write to my CD under the current system.

yep

---

