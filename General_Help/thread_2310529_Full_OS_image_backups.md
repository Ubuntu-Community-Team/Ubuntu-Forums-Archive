---
title: "Full OS image backups"
date: 2016-01-20
forum: General Help
---

### Post by Ghot on 2016-01-20
I tried Ubuntu long ago.  Now, with Windows going the way it is, I'm thinking of dual booting with Windows 7 x64.
Is there a backup software that will work on both Ubuntu and Windows 7?

I have 3 HDD's this is how they are partitioned at present...

[IMG]http://i.imgur.com/Py9iK4s.png[/IMG]


Other questions:
1.  As you can see, I have a big fat 300GB (empty) partition on my 500GB HDD.
2.  What would be the best place to install Ubuntu, for a dual boot scenario.
3.  I use Acronis True Image 2010 for making Win 7 full OS image backups, aka my C: drive. I want to be able to continue doing so.
4.  I assume I must format the 300GB partition to ext4?
5.  On Win 7 I run Bitdefender Internet Security 2016, which I also want to continue to use.
6.  I use Firefox 43.0.4 at present, and have for years.  I only use the extensions NoScript and Classic Theme Restorer.  For Plugins, just Adobe Flash Player.
7.  When Ubuntu is installed I would like to be able to make full OS image backups of that as well...separate from the Windows 7 backups.
8.  I would like to make this as painless as possible.
9.  I do NOT want to do anything to my 2TB HDD's as they are what keeps my system secure (via backups) and has far too much media to lose.
10.  I have Win 7 installed WITHOUT the System Reserve partition, the Page File I don't really care about, I can even run without it.
1..  I have a very stripped down Win 7 install (legit).  I stripped it down myself, over the years.

My system, in case someone sees something I should be concerned with....

Windows 7 Home Premium x64 SP1

AMD FX-8350 Vishera 4.0GHz (4.2GHz Turbo) Socket AM3+ 125W Eight-Core Desktop Processor 
ASUS SABERTOOTH 990FX R2.0 AM3+ SATA 6Gb/s USB 3.0 ATX Motherboard ( 1302 BIOS)
EVGA 06G-P4-2791-KR GeForce GTX TITAN 6GB 384 bit GDDR5
CORSAIR Dominator Platinum 16GB (2 x 8GB) DDR3 1866Mhz RAM (factory settings)
COOLER MASTER Hyper 212 EVO RR-212E-20PK-R2 CPU Cooler (push/pull)

WD 500GB Velociraptor - SATA III	
WD 2TB Caviar Black FZEX - SATA III
WD 2TB Caviar Black FZEX - SATA III
LG GH22LS30 CD/DVD Burner

PC Power & Cooling Silencer 750W Quad EPS12V

DELL Ultrasharp U3011, 30" monitor
Klipsch Pro Media 2.1 THX Speakers (Black)
Ducky DK9008 Shine II Blue LED Backlit Mechanical Keyboard (Cherry MX Black)
Logitech Optical M-100

COOLER MASTER ATCS 840 Full Tower Case
3x230mm, 1x120mm, Optional: 3x Scythe S-Flex SFF21G 120mm (installed)


I've been reading guides on the Internet about dual booting Win 7 and Ubuntu.  However they are written from Win 7 installs, like Win 7 comes out of the box.
If you looked at my Win 7 install you would swear it was Windows XP.


I know this is a lot to ask, and I know most of the questions are probably already answered in these forums...somewhere.


What I'm looking for here, is a simple guide to a best practice method for the dual boot.  Please no links to other guides, as I have read them for years, and to be honest, compared to MY Windows 7 x64 install, they are practically useless.


Thanks in advance.

---

### Post by mastablasta on 2016-01-20
Linux and Windows are two separate systems. whatever you do or run on windows does (usually) not affect Linux. and vice versa.

use the 300 Gb free disk area for Ubuntu. delete the partition for it to be declared free disk space, Ubuntu installer should take care of the rest.

regarding page file [not really Ubuntu topic] - why is it on separate partition at the end of disk? end of disk sectors are slowest.

disk image is just that - an image. Clonezilla or Redo backup can also do it. but, you already have the tool of choice that you use and know, so just keep using it. bit by bit images should be system agnostic.

bitdefender scans for windows files in windows. you won't be able to scan ext4 partition with it.

you say it is a lot to ask, but I haven't seen many questions in your post.

---

### Post by oldfred on 2016-01-20
I know you are copying data from one drive to another for backup, and I do some of that, but that is not real backup. Once you overwrite data then you do not have the old copy which sometimes you want. I then use flash drives & DVDs to make copies of my most important data.

With Windows you just about have to have a image backup as reinstalling & restoring programs & data is difficult. 
But in Linux you can easily reinstall system, so that does not need full image backup, some still prefer it.  If you backup configurations, list of installed apps, and your data then you can quickly reinstall & restore an Ubuntu system. 

Some Windows users suggest:
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

With nVidia, you will need nomodeset boot parameter, but your motherboard may require additional boot parameters. Make sure you have the latest UEFI/BIOS from vendor, that may resolve some of the issues.

 Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)
Most Gigabyte motherboards have issues with IOMMU, but turn that off in UEFI/BIOS and use a boot parameter.

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Any system with multiple drives, I do suggest Windows on one drive and Ubuntu on the other drive. And keep each systems boot loader on the same drive as install. Then if/when one drive fails you can still boot the other drive. 
And smaller system partitions, but larger data partitions. And if dual booting with Windows, you can use NTFS as a shared data partition, so you do not have to copy data to have it in both systems.

---

### Post by Ghot on 2016-01-20
Acronis True Image is weird.  But the more I thought about it....the less worried I am.
If worse comes to worse, I can always wipe the 500GB drive, with DBAN or Partition Wizard boot CD, then use the Acronis boot CD to recover my Windows partition.

My problem is this:  Whenever I boot from the Live CD, the internet ceases to work.  This is not Ubuntu's fault, but mine and my ISP's fault.
The router they offer is...crap.  So I don't use it.  Hence the ISP only sees the MAC address of the LAN chip on my motherboard.

As you can see from the pic above, I have like 10-12 years of files on my storage drives, I would really hate to somehow lose them.

I know that by 2020 Win 7 support will die.  I am planning to switch to Linux, then.
The only thing, I have any issue with is GIMP.  It has a learning curve like Adobe Photoshop, which I don't use either.  I just need a quick and dirty image editor.

Is there such a thing as a milder version of GIMP?  Currently on Win 7, I'm still using Paintshop Pro 7.  I don't even have to think about that, my fingers already do it, without any forethought.

I'm getting too old to learn a new and complex image editor, but I also don't want to be stuck with an editor like MS Paint.

---

### Post by oldfred on 2016-01-20
I install Windows version of Picasa for my wife to use. New versions do not upload to Google due to some new security issue, but we never used that. She likes the editing and browsing that it has, but had learned it from XP back many years ago. You do have to save back to hard drive or otherwise edits are only inside Picasa. I also do not like the default import that most software uses and manually copy from Camera & iphones to my own file structures, which Picasa then finds.

For smaller edits there are many Linux tools.

---

### Post by sgage on 2016-01-20
The free version of Macrium Reflect will make a system image of Linux partitions as well as Windows partitions. I've been using it for years, no problems.

---

### Post by mastablasta on 2016-01-21
image managers: shotwell, digikam

image manipulators: Krita, Pinta, Gimp

Gimp is actually easy to use. there are good tutorials available on web for basic functions. yes, for many users it is a bit overkill. Krita is aimed more at painting, while pinta is like MS paint.

---

