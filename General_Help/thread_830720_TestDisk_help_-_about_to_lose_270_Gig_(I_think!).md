---
title: "TestDisk help - about to lose 270 Gig (I think!)"
date: 2008-06-16
forum: General Help
---

### Post by BrownieBoy on 2008-06-16
Managed to mess things up attempting to install PCLinuxOS on a drive that already contained Windows, Ubuntu Hardy, Kubuntu Hardy and a shared Fat32 drive.  (Does PCLinuxOS not play well with 'buntu?)

Now Gparted shows the drive as "Unformatted", as does Partition Magic (PM) on the Windows side.  PM says there's a disk error and offers to correct it, but if I click "yes" to that, I just get the same error prompt over and over.  If I run PM with the /ipe switch to force it to read the drive the partitions all look fine.  And the partitions are all accessible from Nautilus (or File Manager on Windows), so I don't actually have any immediate problem... except I dare not change anything on the drive, with Gparted thinking that it's empty!!

Here's what I should have on that drive:

1. Windows partition.  Primary, but not actually not actually my booting Windows partition, which is on my other (physical) disk drive, mapped to F: in Windows.  About 40 Gig I think
2. Empty space, where I was going to put PCLinuxOS.  I let PCLinuxOS installer delete the (primary) Gutsy partition that was previously there. I think that was my big mistake.  About 80 Gig
*** the following are in an extended partition *****
3. Ubuntu Hardy. About 60 Gig
4. Kubuntu Hardy.  About 8 Gig
5. Shared FAT32 drive called SHARED2.  About 100 Gig
+ Swap files for the various Linux installs


And here's what TestDisk (running from SystemRestoreCD) now shows:

Disk /dev/sda - 300 GB / 279 GiB - CHS 36483 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  5931 254 63   95297517 [Hard Drive 1]
 3 E extended LBA         15827   2  1 36429 254 63  330987069
 5 L FAT32                23448   0  1 35387 254 63  191816100 [SHARED2]
   X extended             35388   0  1 36429 254 63   16739730
 6 L Linux                35388   1  1 36429 254 63   16739667
   X extended             283176  89  6 290479  89  4  117322694
Must be in extended partition
 3 E extended LBA         15827   2  1 36429 254 63  330987069
   X extended             283176  89  6 290479  89  4  117322694

I'm no expert in deciphering such things, but it looks a mess to me!  How do I get out of this?  I've not used TestDisk before.  Is there a general "fix my f**ked up drive partitons, please" setting?

I downloaded a trial version of Norton SystemWorks for Windows - traitor, I know, but I have happy memories of Norton Disk Doctor from my DOS days!  Disk Doctor offers to fix the errors, but says it's looking for "DOS partitions", so I'm worried it might trash my Linux ones if I let it run.

I've backed up all the important stuff no that drive (I hope!) so I could blow it all away and start again if that's the only option.

Any help gratefully received.

---

