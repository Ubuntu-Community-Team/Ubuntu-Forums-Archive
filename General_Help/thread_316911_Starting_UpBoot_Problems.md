---
title: "Starting Up/Boot Problems"
date: 2006-12-11
forum: General Help
---

### Post by mbikebum on 2006-12-11
Okay, I am a new Ubuntu user and love(d) it.  However I haven't been able to use it for about a week now because of a "Starting Up" problem.  I have a dual boot with both Windows XP and Ubuntu on my hard drive.  When I turn my computer on, it gives me a choice of operating system.  I choose Ubuntu and it goes to a screen that says "Starting Up" with a blinking cursor under it.  It stays like that(for what I assume will be eternity)and never boots.  I can still boot Windows XP though.  I just installed Ubuntu 2 weeks ago and it has had that problem *since* I installed the available updates (there were 28).  I have an AMD processor and I also have anti-virus software on my Windows XP but I determined that it wasn't Symantec that was stopping a boot sector OS other than XP from running (or was it?  Do I need to shut it off entirely?).  I so badly want to use Ubuntu again I was just getting into it!  Please help!

---

### Post by nikolaos on 2006-12-11
I am not sure, but it could be that grub cannot find the partition your ubuntu distro is installed.

When in the grub menu, highlight the ubuntu entry and press e
you should see a line like this
```
root(hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=...
```
press c to get the grub command prompt and type
```
find /boot/vmlinuz-2.6.15-23-386
```
are the numbers(n) in root(hdn,n) the same as in the ubuntu entry in the grub menu?

---

### Post by Cytron D. Corruptor on 2006-12-11
I have almost exactly the same problem.  I installed Ubuntu 6.10 about a week ago.  I am running a dual-boot system with WindowsXP also.   I get the same black screen after the Ubuntu loading logo comes up, a cursor then appears and then a black screen (in about 75%).  The amber log-in screen only appears in about 25% of my attempts to boot into Ubuntu.  WindowsXP appears to be unaffected.

Here are my laptop specs:

Gateway MX7527
Processor: 	Mobile AMD Athlon(tm) 64 4000+  (2.59 GHz)
		Processor FSB up to 1600MHz 	
		Processor Cache 1Mb

RAM Specs:	1 GB (512MB x 2) DDR333 (PC2700)

Graphics:	ATI Mobility Radeon X600 (128 MB)

DVD:		HL-DT-ST DVD -RW  GWA-4082N

HD:		FUJITSU  MHV2120AT PL   (120 GB)

Network adapter:	1394 Net Adapter
			Broadcom 802.11g Network Adapter
			Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller

Interface Type:	RJ-11 Phone Connector		Integrated LAN
		RJ-45 Ethernet Connector	Integrated Modem
		802.11g Wireless Networking	Integrated Wireless LAN	
	
Protocols:	V.92
		802.11g 
	
Audio Chipset:	AC97 2.3 Compatible 


should i format and re-install?  i am a very new user.

---

