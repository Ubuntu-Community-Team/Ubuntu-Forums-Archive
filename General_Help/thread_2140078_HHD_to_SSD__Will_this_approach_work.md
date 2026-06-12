---
title: "HHD to SSD:  Will this approach work?"
date: 2013-04-28
forum: General Help
---

### Post by cigtoxdoc on 2013-04-28
Right now, I have Clonezilla copying the Ubuntu 12.04 and Windows XP partitions of a SATA HD to my WD 500 GB Passport USB drive.  When that is done, I want to put images (?) on a new Crucial M4 256 GB SSD.  Hopefully, I will have a working system when I removed the HD and try to boot from the SSD.

If it doesn't work, where did I go wrong?

Thank you,

John

---

### Post by oldfred on 2013-04-28
XP is not really compatible with SSD.

I wanted to use trim which needs AHCI turned on in BIOS. But my XP does not have AHCI drivers, so I just shut it down (as I had promised for years :) )

Another thread with similar questions
[http://ubuntuforums.org/showthread.php?t=1929727](http://ubuntuforums.org/showthread.php?t=1929727)

 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

   You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.
Info on trim and ext4 without journel 
[http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/](http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/)

   How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

---

### Post by cigtoxdoc on 2013-04-28
Thank you, Oldfred.  thank you for your suggestions.  Right now, my Dell Vostro 3500 laptop has been running on a Crucial SSD for almost a year w/o problems.  I used the Crucial cloning cable and software to do that one.  I still need to figure out how to add Ubuntu w/o killing XP (fortunately, I had an image backup on my Passport drive), because I am taking my business over to Ubuntu and all the HD problems that were keeping Dell service techs busy, have gone away.

I moved a Ubuntu 12.04 64-bit system to another Crucial M4 using Clonezilla without problems.  With 8 GB RAM, no need for swap file (as will be the case for PC waiting for the new SSD), I have not seen the problems others have reported.

John

---

### Post by cigtoxdoc on 2013-04-28
The mission failed.  Clonezilla put out some sort of error message saying something to the effect that target drive was too small.  I added up what I think was saved on the image and it looked like I was I was trying to put 240.43 GB on a 256 SSD.  Maybe I should have used the cloning software that CRUCIAL sends with the SSD?

John

---

### Post by oldfred on 2013-04-29
Some with Windows suggest Windows tools for Windows backup.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

But many have reported good success with Clonezilla.
But if keeping old drive and new drive on same system you will have issues of duplicate UUIDs. Not sure about Windows but with Ubuntu you have to change UUID, then reinstall grub, edit fstab and a few other fixes.

---

### Post by cigtoxdoc on 2013-04-30
I finally got this to work, but I had to stop using Clonezilla.  I used the USB data transfer cable in the Crucial Data Transfer Suite.  I booted the PC from the HDD using the Windows XP side.  Then I used the EZ Gig IV Cloning Software with Data Select Rev. 4.0.4.  That software copied the partitions and files on the HDD to the SDD.  I then used Yannbuntu boot repair disk to get the correct GRUB configuration.  I lost hours playing with Clonezilla, etc.

John

---

### Post by prodigy_ on 2013-04-30
> **oldfred said:**
> Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
Funny, I couldn't find any mention of GPT on that wiki page. :) Either way it'd be strange. The benefits (and limitations) of GPT are well-known and they have nothing to do with SSD.

---

### Post by oldfred on 2013-04-30
@prodigy_
You are correct (it used to) and gpt does not specifically apply to SSD other than it is newer and I believe gdisk supported alignment before some of the other partition tools. One of the main advantages of gpt is that is has a backup partition table, so I primary is damaged you may still be able to read data.

---

