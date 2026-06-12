---
title: "Can't Boot Windows XP - Urgent"
date: 2006-08-04
forum: General Help
---

### Post by Hitchhiker427 on 2006-08-04
(If you want the quick and dirty, scroll down)

My computer setup has been as follows for about a year now:  I have Windows XP (my primary OS) installed on a 160 GB drive identified as hda, and I have Ubuntu installed on a 60 GB drive identified as hdb.  My BIOS allows me hold F11 at startup to select which device I want to boot from.  This eliminates the need for Grub.  I boot to Windows by default, and if I need to boot into Ubuntu, I hold down F11, select the 60 GB drive, and it boots Ubuntu via Grub.  The grub menu is hidden, but has options for my kernel, the safemode, and memtest86+.  

Now for what I did.  I regularly browse this forum looking for cool tricks here and there.  Well, I stumbbled upon [this]("http://www.ubuntuforums.org/showthread.php?t=208855").  I thought it would be cool to get a better looking grub menu for the times I choose to use it.  After following the instructions exactly, nothing worked, so I figured that I screwed up.  So, I tried again.  By reading through the thread I found info about reinstalling Grub and using the commands "root (hd1,0)" and "setup (hd1)".  Well, after things didn't work, I thought that maybe I had hd1 and hd0 mixed up in my head so I tried the other.  In the end, nothing I tried worked.  However, I now had a new (real) problem on my hand.

It seemed that I accidently installed Grub on my Windows XP drive.  So I thought "no biggie, I'll just pop in the install CD and run 'fixmbr'".  Well, I did that, and once I tried to boot up Windows it stopped loading and the screen just said "GRUB".  

Not sure why 'fixmbr' didn't work and I couldn't boot I scoured the internet (on my linux install) for help.  I found one command that I tried from another forum I found on google:  'dd if=/dev/zero of=/dev/hda count=2'.  Unfortunately, this did nothing for me.  I then looked around some more and stumbled upon a program called TestDisk.  While trying to follow the instructions, I was unable to fix anything this way.  When I try to boot to my 160 GB drive it simply loads up Grub, and starts up Ubuntu.

-----

Ok, so now, here's my current situation.  When I try to boot onto my Windows drive, Grub starts up, and loads up Ubuntu (same thing if I try to boot to my Ubuntu drive).  When I run TestDisk, it recognizes both hard drives.  When I go to analyze it says that there are no partition is bootable.  When I go to proceed, it scans (very quickly) and highlights my drive in green.  It recognizes the file system as HPFS-NTFS, and remembers the label I gave my drive (Windows XP).  However, if I try to list the files, it says "Can't open NTFS filesystem: Invalid argument".  

When I run "sudo fdisk -l" it recognizes that an hda exists, and reports the proper size, however it does not list the partition on the drive.  Also, when I run GParted, it says the drive is unallocated.  However, if I run the System > Administration > Disks tool, it sees the drive, and recognizes the file system as Windows NTFS, but will not let me mount the drive.

So, some programs recognize the filesystem and soem don't.  Regardless, I'm not able to access the drive from Ubuntu, and I'm not able to boot to it.  The worst part is that this drive contains quite a few rather important files that I need.  

If anyone has ANY idea what could be wrong, please help.  Thanks in advance!

**Update:**  I tried reading some instruction on TestDisk online and following their instructions.  As a result, I think I made a little bit of progress.  GParted and fdisk recognize my partition properly.  However, when I try to boot Windows it still just says "GRUB" and stops.  I still cannot mount the drive in Ubuntu, and I can't browse the files in TestDisk.  Ok, thanks for reading.

---

### Post by Herman on 2006-08-04
Hitchhiker427, Here's my web-page about how to set up and use GAG Boot Manager, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm").
I recommend you take a look at that and make yourself a GAG Boot Manager floppy disk and set up GAG Boot Manager and run it  from the floppy disk to boot Windows for you.
If you have no floppy disk drive, you can make a GAG Boot Manager CD instead.
If you like GAG Boot Manager, you can install it to MBR later when you are ready.
Good Luck with it, Regards, Herman :D

---

