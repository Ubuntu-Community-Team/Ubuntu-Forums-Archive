---
title: "Need a high-quality FILM scanner supported by Ubuntu-linux"
date: 2007-06-12
forum: General Help
---

### Post by megamania on 2007-06-12
Does anybody out there use a good film scanner with linux?

 I need the following:
[LIST]
[*]scans films (no need to scan printed pictures)
[*]preferably is capable of scanning entire strips of films (like 5 or 10 frames at a time)
[*]works flawlessly under linux
[/LIST]
I'm tempted to go back to traditional photography for a while, but don't want to go back to windows because of that - and can't afford a compatibility-nightmare with unsupported scanners...

---

### Post by megamania on 2007-06-13
Anybody? I really need your suggestions!

---

### Post by cotcot on 2007-06-13
May be look after a second hand Nikon LS (LS40).

---

### Post by megamania on 2007-06-13
> **cotcot said:**
> May be look after a second hand Nikon LS (LS40).

Is it supported natively? What software would work with it?

---

### Post by charles nicholls on 2007-06-13
Nikons are good but the Epson Perfection range cost less (  £138  ) and for most purposes provide excellent scan quality from multiple formats.  Linux is supported and the Digital Ice system for removing defects is really good. Silverfast front end is my preferred pro scan engine but its Windows , Mac only  so the Epson Perfection 4990 Photo which has a 4800 x 9600dpi resolution and 4.0DMax optical density should be more than you need.

:p chas

---

### Post by megamania on 2007-06-13
> **charles nicholls said:**
> Nikons are good but the Epson Perfection range cost less (  £138  ) and for most purposes provide excellent scan quality from multiple formats.  Linux is supported and the Digital Ice system for removing defects is really good. Silverfast front end is my preferred pro scan engine but its Windows , Mac only  so the Epson Perfection 4990 Photo which has a 4800 x 9600dpi resolution and 4.0DMax optical density should be more than you need.

Just to be sure I understand correctly:
-Nikon LS series scanners are supported and work with Linux
-Epson Perfection 4990 works under linux

As far as I understand, Silverfast is a Win/Mac software, so what software am I supposed to use with Linux?

Thanks a lot!

---

### Post by charles nicholls on 2007-06-13
Epson scanners have a linux driver ( [http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm)) 
but I believe you'd have to use xsane which is in the repo's to use the scanner , never used it myself but there should be someone in the forum who has

Epson support 
Perfection 636S 	SCSI 	  	Complete 	US version of GT-7000
Perfection 636U 	USB 	0x04b8/0x0101 	Complete 	 
Perfection 610 	USB 	0x04b8/0x0103 	Complete 	 
Perfection 640 	USB 	0x04b8/0x010c 	Complete 	 
Perfection 1200S 	SCSI 	  	Complete 	 
Perfection 1200U 	USB 	0x04b8/0x0104 	Complete 	 
Perfection 1200Photo 	USB 	0x04b8/0x0104 	Complete 	with TPU
Perfection 1240 	SCSI USB 	0x04b8/0x010b 	Complete 	 
Perfection 1640 	SCSI USB 	0x04b8/0x010a 	Complete 	 
Perfection 1650 	USB 	0x04b8/0x0110 	Complete 	 
Perfection 1660 	USB 	0x04b8/0x011e 	Complete 	 
Perfection 2400 	USB 	0x04b8/0x011b 	Complete 	 
Perfection 2450 	USB IEEE-1394 	0x04b8/0x0112 	Complete 	
erfection 3200 	USB 	0x04b8/0x011c 	Complete 	US version of the GT-9800
Perfection 4870 	USB 	0x04b8/0x0128 	Complete 	US version of the GT-9800
Perfection 4990 	USB 	0x04b8/0x012a 	Complete 	US version of the GT-X800
Expression 636 	SCSI 	  	Complete 	US version of GT-9500
Expression 800 	SCSI 	  	Complete 	  



nikon support
Nikon 	LS 30 	SCSI 	  	Complete 	working -- model available to developer
LS 2000 	SCSI 	  	Good 	 
LS 40 ED 	USB 	0x04b0/0x4000 	Complete 	 
LS 4000 ED 	IEEE-1394 	  	Good 	needs linux kernel 2.4.19 or later
LS 50 ED 	USB 	0x04b0/0x4001 	Minimal 	 
Coolscan V ED 	USB 	0x04b0/0x4001 	Minimal 	 
Super Coolscan LS-5000 ED 	USB 	0x04b0/0x4002 	Untested 	May work, similar to LS 50 ED, but untested. Please tell us if it works.
LS 8000 ED 	IEEE-1394 	  	Good 	needs linux kernel 2.4.19 or later

---

### Post by megamania on 2007-06-15
> **charles nicholls said:**
> nikon support
Nikon 	LS 30 	SCSI 	  	Complete 	working -- model available to developer

thank you very much for your information.

The funny thing is that the scanner that has best support (LS30 SCSI) is the one I sold a couple of years ago!  :-|

---

### Post by Spoofhound on 2007-06-17
I've been using a Nikon Coolscan IV ED (LS 40) under Ubuntu for quite a while. I have used it initially with XSANE which worked fine. I then moved to the Linux version of Vuescan ([www.hamrick.com](www.hamrick.com)) which gives much better results. Vuescan is however a commercial, closed-source product- but in my view worth the cost.
Hope this helps

---

### Post by megamania on 2007-06-18
> **Spoofhound said:**
> Vuescan is however a commercial, closed-source product- but in my view worth the cost.
Hope this helps
Thanks Spoof,

I think I'll look for a LS40 then. When I had a LS30 I tried Vuescan (Windows version) and was quite impressed with it.

Can you tell me how many negatives can the LS40 scan at a time? That's a very important issue to me.

---

### Post by prankst3r on 2007-06-18
I own an Epson Perfection 4990 PHOTO scanner and it runs quite nicely under Ubuntu (currently running 7.04 64-bit version). However, the Digital Ice technology for this scanner is _not_ supported. I have VMware installed on my box running Windows XP so I can run Silverfast if I need to use Digital Ice to remove artifacts on photos. The downside to using Silverfast in a vmware setup is that it runs about 25-30% as fast as a real Windows install.

I really wish Epson would include Digital Ice support in their Linux driver so someone could develop software to take advantage of it.

---

### Post by Spoofhound on 2007-06-19
> **megamania said:**
> Thanks Spoof,

I think I'll look for a LS40 then. When I had a LS30 I tried Vuescan (Windows version) and was quite impressed with it.

Can you tell me how many negatives can the LS40 scan at a time? That's a very important issue to me.

The LS40 has an adapter that takes a 6 frame length of film. I only scan slides so I have no idea how effective this is. As far as I know some of the other Nikon scanners such as the Coolscan 5000 (much more expensive) can also take a film roll adapter. The older Coolscan 4000 also takes a roll adapter - don't think its sold by Nikon anymore but should be available on eBay.

---

### Post by mutzinet on 2007-12-02
Bumping this thread again for a similar question: Has anybody tried the Nikon LS50 with Vuescan? Scanning quality of the LS50 should be much better than the LS40, but I haven't heard of any linux users yet. Anybody here?

Thanks :)

---

