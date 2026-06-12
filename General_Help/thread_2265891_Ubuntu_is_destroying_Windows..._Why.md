---
title: "Ubuntu is destroying Windows... Why?"
date: 2015-02-18
forum: General Help
---

### Post by 777funk on 2015-02-18
I'm almost to the point of saying good bye to Ubuntu. I hate to do it because I've used it for the day to day for 3-4 years now. I still need Windows for certain programs (audio/video production and CAD). So even though I don't prefer Window's functionality, I don't know what else to do but ditch Ubuntu.

Here's what I've got for a setup:
-Win 7 on one hard drive (ASUS factory install with a separate data partition that THEY created)
-Xubuntu on a second hard drive

Here's the problem:
When I start Windows (no grub but choose the proper HDD from BIOS) I'm getting Check Discs and files fixed. After this happens there are major software problems and some programs disappear or no longer work! I'm having to re-install and loosing progress. I do access and create data on the Win 7 Data Partition (separate partition created by ASUS that shipped with the computer) from Ubuntu. 

When I installed Xubuntu it wouldn't install without using UEFI. Here's the bootinfo report:
[http://paste.ubuntu.com/9679004/](http://paste.ubuntu.com/9679004/)

I'd **hate** to go back to Windows, but if I can't track this problem, I don't know what else to do. I certainly can't afford for my Win 7 system to be constantly getting trashed.

EDIT: ANother interesting detail... in Windows the time keeps changing to  the wrong time zone (which is also the time in the BIOS screen). I can  reset the time to correct (internet time) but it just keeps going back  every restart.

If anyone has the ideas toward a solution it would be very appreciated!!!

---

### Post by coldraven on 2015-02-18
> I'm getting Check Discs and files fixed.It could be that the Windows drive is failing. Use some windows utility to check the SMART data on that drive or boot into Ubuntu and check it from there with "Disks".

> I do access and create data on the Win 7 Data Partition (separate  partition created by ASUS that shipped with the computer) from Ubuntu.
I'm not an expert in this field but in these threads they mention GPT and creating files with characters that Windows does not understand.
[http://ubuntuforums.org/showthread.php?t=2116550](http://ubuntuforums.org/showthread.php?t=2116550) see post #14 for a way to edit fstab to stop the bad filename problem.

---

### Post by 777funk on 2015-02-18
I guess one easy way to determine if indeed the disk has problems would be to use ONLY windows for a few weeks/months and see if the problem persists. I don't have any trouble Reading/Writing to or from the Data partition on this drive (the Win7 factory Data partition) FROM Linux. This is where I came to the conclusion that Linux is the cause here. Window isn't liking something Linux or the dual drive setup is doing. I don't understand How since they're on seperate drives.

---

### Post by ajgreeny on 2015-02-18
I don't really know windows any more but does Win 7 use the hybrid-hibernation shutdown instead of a full shutdown the same way as the default for Win 8?

If you managed to run Xubuntu from the state when Win 7 is not fully powered off that would certainly cause the sort of problem you are seeing.

---

### Post by SeijiSensei on 2015-02-18
If you boot into Linux you can use the SMART tools to look at your drives' conditions.  Install and run them like this:
```

sudo apt-get update
sudo apt-get install smartmontools
sudo smartctl /dev/sda -a | more
sudo smartctl /dev/sdb -a | more
[etc. if you have more than two drives]

```
You might want to pipe the SMART output to "more" as I do above and page through it with the space bar.  I have one drive with a couple of errors from its first use, and the amount of detail each error generates is substantial.

I assume you're always shutting down Windows correctly and not turning off the power.  That will trigger a Windows rescan of the filesystems.  Is Windows checking your discs when you reboot?  What if you shut down Windows cleanly from the interface, boot into Linux, cleanly reboot from there, and boot Windows once more?  Does it still run a file system check even then?  Can you see which drives are checked, the system drive or drive D?

---

### Post by 777funk on 2015-02-18
Each time I reboot I always cleanly "shut down" each system. I've heard about the hybernation issue with Windows. 

I'll check the SMART tool. Thanks! Hadn't heard of that one.

EDIT: here's what the SMART tool has to say about the Win7 drive:

> === START OF INFORMATION SECTION ===
Model Family:     Toshiba 3.5" HDD DT01ACA...
Device Model:     TOSHIBA DT01ACA100
Serial Number:    Z38JB4MPS
LU WWN Device Id: 5 000039 ff7d5874b
Firmware Version: MS2OA7L0
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Feb 18 14:43:48 2015 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled



---

### Post by oldfred on 2015-02-18
Are you directly writing into the Windows system partition ( c: "drive" ) or into a separate NTFS data partition.
For whatever reason Windows is not always happy with use of the System partition.

Also part of issue is user related as Linux NTFS driver shows all the normally hidden in Windows files & folders. In Windows I used to turn show those on, and had issues only using Windows.

---

### Post by 777funk on 2015-02-18
> **oldfred said:**
> Are you directly writing into the Windows system partition ( c: "drive" ) or into a separate NTFS data partition.
For whatever reason Windows is not always happy with use of the System partition.

Also part of issue is user related as Linux NTFS driver shows all the normally hidden in Windows files & folders. In Windows I used to turn show those on, and had issues only using Windows.

I don't "think" I am. ASUS had factory installed Win 7 with a separate DATA partition but this was done in the factory and probably Windows did this partitioning. I'm only writing to this partition titled DATA. 

Here's what fdisk -l has to say about that drive:
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    48383999    24088576   1b  Hidden W95 FAT32
/dev/sda3        48384000   829790207   390703104    7  HPFS/NTFS/exFAT
/dev/sda4       829790262  1953520064   561864901+   7  HPFS/NTFS/exFAT

Also attached is GParted's View of this drive.

---

### Post by 777funk on 2015-02-19
Ahhh!! Man I like the tools in Linux but it's just too much of a hassle to balance both OS's happily. I've run into lots of problems besides the one I mentioned. Sometimes Mozilla isn't happy about shared profiles and just won't open the correct profile for no reason. Sometimes files get messed up or are incompatible between two OS's. 

I think if Linux was ONLY used, it'd be great. But a dual boot just seems to be a problem. Too bad about this because in every other way, I think Linux is a great OS. I guess it could be said that Windows also doesn't play nice with Linux and in many other ways it's a great OS. In any case, it's definitely headache at times with running both on the same machine. Guess there's no perfect world with computing.

EDIT: This problem gets **_worse yet_**! I noticed when Windows 7 runs it's CHKDSK that it deletes files that were created from Ubuntu. I had an HTML webpage saved from Firefox (happens to be an obit from a friend who was recently killed in a car accident) and the CHKDSK decides that that file needs to be deleted. I watched it from the repair screen in Windows, then sure enough it's gone. This is probably why my applications in Windows are having issues. 

I have it backed up on another drive... but still... this has me pulling my hair out. Too much of a pain to deal with stuff like this I'm afraid.

The only conclusion I can come to is that Windows still uses the separate DATA partition as part of it's OS. So it's not really like having a real separate partition since it was a Factory made (probably in Windows) DATA partition.

---

### Post by dragonfly41 on 2015-02-19
Can you try SpiderOak to sync (or share) between Windows and Linux rather than direct writing Ubuntu>Windows?

---

### Post by oldfred on 2015-02-19
I shared my Firefox & Thunderbird profiles since 2006. Back then it was XP and I would copy profiles to laptop & back for travel. So two different XP and two different Ubuntu.  I now have 12.04 on laptop & 14.04 on Desktop and have not had any issues. I have been surprised that even minor version differences between installs have not caused issues.
But I do a lot of clean up of profiles to remove old emails & separately run sqlite vacuum on all the sqlite files with a script.

---

### Post by 777funk on 2015-02-19
I think the biggest problem here is that there are 2 partitions (a separate DATA partition) but it must have been created in Windows and for some reason Windows isn't liking that it's written to even though it's separate (at least appears to be) from the actual Win7 OS partition.

---

### Post by Mark Phelps on 2015-02-19
Win7 does not use the new Hibernation method of Win8, if it did, you would not be able to mount the partitions in Ubuntu.

The sda3 partition is your Win7 OS partition and you should NOT be mounting that in Ubuntu, unless you go to the trouble of mounting it read-only.  That is most likely the cause of the frequent chkdsks in Windows. Mounting a Windows OS partition read-write in Linux is asking for file system corruption.

---

### Post by 777funk on 2015-02-19
> **Mark Phelps said:**
> Win7 does not use the new Hibernation method of Win8, if it did, you would not be able to mount the partitions in Ubuntu.

The sda3 partition is your Win7 OS partition and you should NOT be mounting that in Ubuntu, unless you go to the trouble of mounting it read-only.  That is most likely the cause of the frequent chkdsks in Windows. Mounting a Windows OS partition read-write in Linux is asking for file system corruption.

I don't write or even access sda3 (only sda4). So I'd assume that it's not being touched, no?

It's sda4 (DATA partition factory installed on the same drive as Windows) that I read/write to and it's having issues when Windows boots. Window's ChkDsk feels the need to delete files made by Ubuntu on this partition.

---

### Post by dragonfly41 on 2015-02-19
This similar symptom has been reported here ... 

[http://www.linuxquestions.org/questions/linux-newbie-8/windows-chkdsk-deletes-files-written-by-ubuntu-on-an-ntfs-partition-913606/](http://www.linuxquestions.org/questions/linux-newbie-8/windows-chkdsk-deletes-files-written-by-ubuntu-on-an-ntfs-partition-913606/)

---

### Post by Mark Phelps on 2015-02-19
> **777funk said:**
> I don't write or even access sda3 (only sda4). So I'd assume that it's not being touched, no?

It's sda4 (DATA partition factory installed on the same drive as Windows) that I read/write to and it's having issues when Windows boots. Window's ChkDsk feels the need to delete files made by Ubuntu on this partition.

Sounds like some form of hibernation is being activated when you leave Win7 -- as when that happens, Windows saves a copy of the partition table of all open NTFS volumes and, when Windows is then restarted, overwrites the current partition tables with the ones it saved.

Typically, when you have a dual-boot machine, in Windows, you have several shut down options: shut down, restart, sleep, hibernate.  If you use restart to close Win7, that may be the problem, as you should really use "shut down".  IF you are using "shut down", then my suggestion would be to post your concerns on a Win7 forum -- [www.sevenforums.com](www.sevenforums.com) is one of the best.

---

### Post by 777funk on 2015-02-19
Thanks! And yes I am restarting at times with Win7. I don't use Hibernate specifically because of the problems I've read about. But it sounds like maybe shut down is the only real option. Interesting there. I still suspect that something maybe is not quite right with the way Windows 7 has the 2 partitions (OS and DATA) since it was done at the factory on this ASUS machine. I just wish I could figure out the why on this. I'll experiment with shut down instead of restart. At this point, I'm a little afraid to use Ubuntu because things keep breaking and files are getting lost. I have everything backed up, but it's still a mess to have to keep fixing. And of course if something important disappears without notice (it's impossible to track millions of files), that could also be a problem.

---

### Post by dragonfly41 on 2015-02-19
Another possibility .. install VirtualBox in Win and then install Xubuntu as VM in VirtualBox.

---

### Post by leclerc65 on 2015-02-19
I have been in the same boat.
Now I keep the two environment separately, one NTFS data partition for Windows, and one EXT4 data partition for Linux.
The NTFS partition is expendable that is used  as a dump for files that don't play well in Linux (PPS for example), as for serious (sic) Windows files I keep
them in the C drive that is not mounted, out of touch of Linux.

---

### Post by 777funk on 2015-02-20
Sounds like there can be some issues here. I wonder if I were to backup the DATA partition that was set up from the factory on the same drive as the OS Partition and re-create the partition from GParted then reload the data, if my problems would be fixed.

ANother interesting detail... in Windows the time keeps changing to the wrong time zone (which is also the time in the BIOS screen). I can reset the time to correct (internet time) but it just keeps going back every restart.

---

### Post by sudodus on 2015-02-20
In some computers (with dual booting) I use a common NTFS ***data*** partition. It works well for me.

The time problem is probably that Ubuntu assumes that the computer clock is set to the universal time, UTC, and then translates to your local time, while Windows assumes that the computer clock is set to the local time. And the two systems are fighting and resetting the clock ...

---

### Post by 777funk on 2015-02-20
Looks like you're right on the time issue and I think that took care of it. Specifics on what I did for that here:
[http://askubuntu.com/questions/305313/system-time-keeps-resetting-to-utc](http://askubuntu.com/questions/305313/system-time-keeps-resetting-to-utc)

---

### Post by SeijiSensei on 2015-02-21
I wouldn't be surprised if the difference in time zones caused Windows to check the filesystem at boot especially if the timestamp is in the future.  I'm in UTC-5 so if I were to write a file from Linux with a UTC date, Windows should see that as an error and rescan the drive.  Let us know if fixing the clock also fixes the problem with the drive being frequently rescanned.

---

### Post by 777funk on 2015-02-21
> **SeijiSensei said:**
> I wouldn't be surprised if the difference in time zones caused Windows to check the filesystem at boot especially if the timestamp is in the future.  I'm in UTC-5 so if I were to write a file from Linux with a UTC date, Windows should see that as an error and rescan the drive.  Let us know if fixing the clock also fixes the problem with the drive being frequently rescanned.

Interesting! Wouldn't that be nice if that was it. I've been in Win7 for a few days now. I'll go back to Ubuntu and see what happens. I wouldn't be surprised if you're right!

---

### Post by westie457 on 2015-02-21
> **777funk said:**
> I think the biggest problem here is that there are 2 partitions (a separate DATA partition) but it must have been created in Windows and for some reason Windows isn't liking that it's written to even though it's separate (at least appears to be) from the actual Win7 OS partition.

Are you unmounting the DATA partition before shutting down Ubuntu?
If not, that could be the cause of the Windows CHKDSK and subsequent removal of files.

---

### Post by ajgreeny on 2015-02-22
> **westie457 said:**
> Are you unmounting the DATA partition before shutting down Ubuntu?
If not, that could be the cause of the Windows CHKDSK and subsequent removal of files.
It is totally necessary to specifically or manually unmount any partition that you have mounted in Ubuntu when you shutdown the OS; it is always done by default at shutdown without any input needed from you.

If that were not the case it would result in huge problems for everybody every time the system was shutdown!

---

### Post by 777funk on 2015-03-03
Seems things are working better now that the time issue has been fixed in Ubuntu. Interesting!

I'm going to give it a few months of regular dual usage before I call it good/solved.

---

