---
title: "Systems slow after Feisty installation."
date: 2007-06-05
forum: General Help
---

### Post by siva214215 on 2007-06-05
Hi, everyone.  I like the new Feisty since it is fast compared to the older versions.

	In our office we are having 24 systems.  2 celeron 2.6, 4 celeron 2.4, 18 celeron 1.0 GHz systems,  all of them are via chipsets with 256MB RAM(DDR).  All the systems will be running for 16 hours continuously.  Firefox will be used continuously all the time for internet with 5-15 windows opened.  Frequently evince will be used for pdf viewing.  
	When we were using ubuntu 6.10 all of them working fine.  When I tried to install 7.04 Fiesty the problems started.

	For the 1.0 GHz systems (they were quite old, nearly 1 year older) were stopped at busy box.  Then I tried 
[B]		modprobe ide-generic
		modprobe ide-disk[/B]
	later
		**update-initramfs -u** (with piix, via82cxxx, ide-disk, ide-generic in modules file)
	
	and feisty installed.
	I had updated the Xorg driver from vesa to via and even updated the kernel.
	I used **hdparm -c1 -d1 -k1 /dev/hda** on all systems to get more performance.

	Systems will work well and with good speed for sometime.  But what happening is that the systems are  becoming too slow specially when trying to open pdf files from firefox.  When I observed the system monitor it is showing uninterruptible processess which are causing the problem.  Whenever a process is going into uninterruptible state the systems are becoming very slow.  The processes which frequently that will go into uninterruptible status are kjornald, kswapd0 and firefox-evince.  How can I reduce this?

	I am tired of firefox which is becoming very slow after sometime (nearly 2-3 hours).  The worst scenario is when trying to open pdf files from the firefox (using any pdf viewer, default is evince).  I know that 256MB quite sufficient for the systems.  I tried with some tweaks like **vm.swappiness**=(0-10).  The systems never crosses 200 MB of RAM and 20-30 MB of swap in usage.  The same systems are working well with windows.  But we want to stay with Ubuntu.

	I tried for a long time since the release of feisty.  But I got the solution no where.  So I am posting this hoping some help|suggestions.  Feisty is really good and fast compared to the old versions.

---

