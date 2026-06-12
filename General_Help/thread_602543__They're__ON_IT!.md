---
title: "_They're_ ON IT!"
date: 2007-11-04
forum: General Help
---

### Post by dburnett77 on 2007-11-04
many, many remaps going on:

dburnett@dburnett-desktop:~$ lsusb
Bus 005 Device 002: ID 054c:0243 Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04b8:0818 Seiko Epson Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
dburnett@dburnett-desktop:~$ 



currently their crashind ID's on the USB adapter, via IDE+AGP ports.

Once a large pool is established, a phony device shows:

dburnett@dburnett-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
03:01.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
dburnett@dburnett-desktop:~$ 

I'd say this is the culprit, now:

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)

as I only have the SoundCard, no other PCI.

Watch your tick cycles.  Quite interesting to display system usage, and access Yahoo!'s web site.

---

### Post by Nano Geek on 2007-11-04
Uhh, What?

---

### Post by n3tfury on 2007-11-04
how about being more clear on what "they" are "on" about?

---

### Post by bapoumba on 2007-11-04
Hmm, yes. Moved to "General Help" in the meantime.

---

### Post by dburnett77 on 2007-11-04
Dude of 3 above, at least use the correct forum symbols for the status of posts:  I'm aware that JAVA hacks are predominant, and you obviously like coffee.  But this forum uses different symbols to indicate the status you so gladly seek for yourself.

And, I guess to throw the current claimer:  Must be crazy and paranoid.  As their are absolutely no naughties, and no one would ever, ever, think of hacking or otherwise doing BAD things.  Imbecile.

---

### Post by Nano Geek on 2007-11-04
OK, thanks? :confused:

---

### Post by hikaricore on 2007-11-04
.... I have no idea what the hell this is.... but I fixed your title...

*looks confused and walks off*

---

### Post by Crafty Kisses on 2007-11-04
I don't get this...

---

### Post by hikaricore on 2007-11-04
Boy needs a tinfoil hat me thinks...

---

### Post by dburnett77 on 2007-11-06
Yeah, _fsck_ has worked wonders for me.  Around its que, I'd noticed it run.  the -f switch was awesome.  Hey!, I do feel better, maybe it was a case of the heebie-jeebie'ss.

Glad, there's no hackers.  Man, I sweat all that for no reason...

---

### Post by nixclusive on 2007-11-06
duh.. what's going on in here?

---

### Post by dburnett77 on 2007-11-06
Look, man, go on home.  The show's over...

---

### Post by dhtseany on 2007-11-06
Hi!

I'm posting stupid comments that relate nothing to the thread and insult people's intelligence!

Sean

PS- [Link]("http://ubuntuforums.org/showthread.php?p=3716695")

Annoying, isn't it?

Moron.

---

