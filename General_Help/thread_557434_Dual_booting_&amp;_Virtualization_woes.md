---
title: "Dual booting &amp; Virtualization woes"
date: 2007-09-22
forum: General Help
---

### Post by aletheianalex on 2007-09-22
Hello.  I was not sure which category to place this post in, so I chose "general"

I had Ubuntu installed on a secondary machine (old Sager notebook), and I decided to set up my desktop machine (Mac Mini Intel) to dual boot OSX/Ubuntu as opposed to the OSX/XP Pro scheme that I had been running.

Anyway, I had OSX/XP running so that I could boot from either machine at startup, AND I could also run XP alongside OSX in a virtualized window within Parallels off my Boot Camp partition, so that I could make changes and configure the system while still using OSX as the primary OS.  This setup made life SOOOOO much easier than having to reboot the whole system constantly... so I would like to do the same with the new OSX/Ubuntu scheme.

I have re-partitioned the 60G SATA drive as 40G HFS+ OSX partition (with the small EFI boot partition that Apple adds) as well as a 20G FAT32 partition for Ubuntu, which is split with a 1G 'swap' space. I have installed rEFIt as my bootloader.  This setup works fantastically well for choosing an OS at startup, and I have configured Ubuntu for my hardware with no snags whatsoever... I can boot from either system without trouble and all my hardware works normally under both.

HOWEVER, I have hit a few snags running the same Ubuntu in a virtualized window from the partitioned disk.  I hacked the Parallels .pvs configuration file to recognize the new partition map, and have also installed ExtFS so that I can mount the Ubuntu partition (but not edit it) on my OSX desktop so that I can view all my Ubuntu files and configurations.  I can boot into GRUB from Parallels, but I am not using GRUB as my bootloader, so there is obviously no conf file.  I tried booting Ubuntu from parallels using my Apple EFI partition, but that froze up immediately.  Under GRUB, I pointed the root to the proper partition, and directed it to the proper kernel and ran 'boot'.  It loads somewhat, but obviously does not run the configuration properly, and it eventually fails to boot.

So the question is:  should I dual-boot using rEFIt, and then somehow copy that boot configuration file over to GRUB in order to boot Ubuntu in a virtualized window within OSX (I would just try it, but I can't find any information as to whether that would scramble my system having two boot configurations), OR is there a way to get my current rEFIt configuration to boot Ubuntu within Parallels?

Thanx.

---

### Post by aletheianalex on 2007-09-23
Nevermind... it is a bug in Parallels.  I downloaded a trial of VMware Fusion and got it set up and dual booting AND virtualizing in about 5 minutes.

---

