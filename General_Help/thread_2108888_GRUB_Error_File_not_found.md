---
title: "GRUB Error: File not found"
date: 2013-01-25
forum: General Help
---

### Post by RememberWhenItRained on 2013-01-25
Apologies if this is in the incorrect thread:

[Windows 7/8 & Linux Triple boot - GRUB error: File Not Found]("http://www.reddit.com/r/techsupport/comments/17ai78/windows_78_linux_triple_boot_grub_error_file_not/")
[URL="http://www.reddit.com/r/techsupport/comments/17ai78/windows_78_linux_triple_boot_grub_error_file_not/"]
[/URL] 
I done goofed.
  I'll be frank, I'm an ITEC major but now screwed up my system because I was being sloppy.

  I'll try to present this in the most easy/concise format as possible. Here goes:
  System: Dell Inspiron 1440; 500GB HDD; 4GB DDR2 RAM, Intel Pentium Dual Core OSes: Windows 7, Windows 8 (no longer, more on that later), Ubuntu Linux (12.04)
  
What Happened: I have been triple booting with two linux distros and  Windows 7 (my default OS). A few mos back I decided to test out windows 8  and loaded the OS on a separate partition (I don't remember how much  space I allocated for it, nor what the default amount was).
  Due to my poor forethought, I had not partitioned the space  effectively and was running out on my Win7 partition while i had some  90GB unallocated. So, in an effort to clean up GRUB and remove some  space, I decided to remove Win8. Didn't like it so much anyway.
  
I began to follow [these steps]("http://superuser.com/questions/395719/how-do-i-uninstall-windows-8-consumer-preview")  to remove the OS.  I was rushing (dumba.. move, i know) and closed the  tab prior to completing all the steps. I fired up the Disk Manager and  deleted the partition labeled as Windows 8. The odd thing was that it  was only a very small amount of space. Something like 86MB. Was not sure  if this was normal, but didn't give it too much scrutiny as I had not  stored any files on the local (Win8) partition. However, I did not select Shrink Volume Before I closed Device Manager.
  
Now to the present:  When I hibernated my Win7 OS (which always results in an improper shutdown) the message I receive is
GRUB error: File Not Found
GRUB Recovery>

  I'm thinking/wondering if i deleted the wrong partition (perhaps a bootloader.)
  I would try to do a system restore, but since i cannot access Windows, that's out.

  I have Ultimate Boot CD and am booted in Parted Magic, ATM. I also have a Windows 7/8 Repair Disc.
  Would Either of these help. My external HDD has someone else's backup data, so i cannot backup (to an HDD) ATM.
  Would using either rescue disc cause me to lose my data
  I have /home as a seperate partition, as well as data on C:
  Thoughts/ideas?
  Thanks in advance.
  **TL;DR:** Tried to remove Win 8, probably goofed, bootloader won't load.

---

