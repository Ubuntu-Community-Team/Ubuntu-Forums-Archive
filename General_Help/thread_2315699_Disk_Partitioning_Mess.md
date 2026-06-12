---
title: "Disk Partitioning Mess"
date: 2016-03-01
forum: General Help
---

### Post by Biltron on 2016-03-01
Okay, first time poster but long time fan.  I got a refurb Lenovo T430s notebook around a year ago, and it came with Windows 7 installed on it, on a WD 7200rpm 320GB internal SATA drive.  I of course prefer to use Linux whenever possible, and I happened to have a 32GB mSATA SSD drive sitting around doing nothing.  So, I install that in the laptop, then boot up with an Ubuntu 14.04 live CD, and install it to the SSD (I figured might as well have the OS I use the most on the faster drive).  It automatically set itself up so it would boot from the mSATA, and give me a GRUB menu, asking if I wanted Ubuntu, or Windows (on the WD magnetic drive).  So, that was my starting point.

Then, over the weekend, I purchased a 480GB SATA3 SSD (2.5" form factor).  My intention was to copy the partitions from the 2 drives currently in the laptop onto this new drive, and have a nice dual boot machine where everything is running at the formidable pace of SATA3 speeds.

Here are the partitions in each drive, in case anyone is wondering.

_mSATA 32GB SSD  (installed by me, Ubuntu installed onto it, dual boot set up)_                                                 
/dev/sdb1  ext4   mount="/" 
/dev/sdb2  extended 
     ---/dev/sdb5  linux-swap 
                                                                          

_WD 7200rpm 320gb  (the windows install, from the store)_
/dev/sda1  ntfs   "recovery"
/dev/sda2  ntfs   "SYSTEM"
/dev/sda3  ntfs   "Windows"
/dev/sda4  ext4   mount="/HOME"

So, I basically copied the first 3 windows partitions from the WD drive to my new 2.5" SSD, then made an extended partition to hold the linux partitions (root, home, and swap).

My 480GB 2.5" SSD now has this structure:

[ATTACH=CONFIG]267598[/ATTACH]

I then used the "Boot Repair Live" CD to get GRUB working again.  And Ubuntu works fine. But if I try to boot into windows I get a "Windows Boot Manager" error, saying "Windows failed to start.........info: The boot selection failed because a required device is inaccessible."

I'm sure I did at least one step wrong, cloning a single drive is easy enough, but I'm having a HECK of a time getting this to work.  

ANY advice would be appreciated.  I asked my professor at school who taught my operating systems programming course, and even he wasn't sure how to do this.

If you read this, thank you.  If you are going to offer advice, double thank you.

-NDubs

---

### Post by Bucky Ball on 2016-03-01
Was Windows 7 hibernating when you copied it?

You say you copied partitions then copied them back to another drive. What software did you use to do this? Was the install in UEFI or BIOS mode?

Generally Windows issues with Win bootloader need to be fixed with Windows tools so hopefully someone can shed more light on that. 

Off-topic but worth mentioning: Why do you have such a huge /swap partition? Unless you are hibernating so you can boot quickly, and Ubuntu and grub boot quick enough, especially on SSDs, you only need 2Gb, and if you have a lot of RAM installed, that is more for show (some users don't have a grub at all).

---

### Post by Biltron on 2016-03-01
I'm not sure what you mean by if windows was hibernating when I copied it.  I copied partitions using GPartEd, while running off a Ubuntu Live CD.  And yeah the swap size is enormous haha.

---

### Post by Biltron on 2016-03-01
I am temporarily going back to what DID work for me, which was cloning the entire WD 7200rpm 320GB drive (with Windows install, as well as my EXT4 /Home partition) to the new 480GB SSD using Clonezilla.  I did that before and it worked just fine.  I only tried to put everything on the new SSD because some part of me was really bothered by the fact that my Linux install can only run at SATA-II speeds (apparently on this laptop, the mSATA can only achieve 3Gbps, while the actual SATA drive bay can do SATA-III 6Gbps).  But if someone can tell me where I went wrong (it may have been everywhere) and/or tell me if what I want to do is possible, that would be great.

Keep in mind I can't reinstall Win7, hence going through all this work.  That, and I don't want to re-config and re-customize EVERYTHING, it takes HOURS!  (You fellow computer guys know that pain)

---

### Post by Biltron on 2016-03-01
Update- cloned the functional WD 320GB onto the new SSD using Clonezilla, Windows STILL wont boot now.  GRUB menu DOES show up, and Ubuntu will boot.  So apparently the Windows boot sector/manager/whatever the heck it is, is not correctly set up?  I'm guessing?

---

### Post by oldfred on 2016-03-02
You may need to run a full set of Windows repairs including chksk. 

 Manually create repair flash, shows files & locations
[http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools](http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools) 

 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 
   [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Biltron on 2016-03-02
Thanks for the tips oldfred, I looked them over.

UPDATE:  As silly as this is, even though a Windows 7 disc wouldn't repair the boot issue (probably since I downloaded the ISO and burned it, so god only knows if its real or not), I made a "system repair disk" from my OTHER laptop running Win7, from the "Backup" control panel.  Booting up with THIS disc on the problematic machine (with only the windows drive installed in the unit), it found errors, fixed them, and rebooted.  All of a sudden I was booting into windows OFF OF MY HDD, not from a CD!  

The simplicity of the solution is almost maddening.  But I am elated that I could fix it, and it only took that.

I still want to put both Linux AND Win7 on the same drive (my new SATA-III SSD 480GB), but I'm a little afraid of messing stuff up after this debacle.  Thanks to the few who actually contributed!  I appreciate it.  Together, we can all increase our knowledge.

---

### Post by oldfred on 2016-03-02
Keep working Windows repair disk, Boot-Repair fixes Linux issues and only a few minor Windows issues.

Use Windows own partition tools to shrink the NTFS partition and reboot immediately so it can run chkdsk. Then use gparted to create partitions in advance or just use installer if you only want / & swap. With BIOS and MBR you have to only use 4 primary partitions and one of those should be the extended partition.

---

### Post by Biltron on 2016-03-02
The whole issue was the drive with windows on it got its bootloader/MBR messed up at some point.  Even with ONLY that drive in the computer, it would give the same error, which helped me rule out any kind of GRUB issue.  The windows recovery disk did something (I really wish I knew what) and now that drive is bootable again.  Guessing the MBR got hosed, or the windows bootloader had some kind of issue.  I DID notice that the "SYSTEM" partition on the drive (marked boot, only about 250MB) seemed to be almost empty.

Everything works fine now, I just wish I could have both OS's on the same drive.  But I am NOT going to mess with that, at least not until I know I'm gonna have a large amount of free time

---

