---
title: "help getting online via ethernet"
date: 2008-03-31
forum: General Help
---

### Post by HeadLikeAHole531 on 2008-03-31
i have a problem getting online on ubuntu, im not sure why it wont work. i have a compaq presario SR1603WM. a 75 gb hard drive with xp installed on it, and another 20 gb hard drive with ubuntu. i have a realtek network card, and i use a linksys wireless router (for a seperate laptop). can anyone help me get online on ubuntu?

---

### Post by Slushdoot on 2008-03-31
Open a terminal window and type
lspci
and paste the results here.  That'll tell us what model network adapter you have.

---

### Post by HeadLikeAHole531 on 2008-03-31
okay, i will. any easier way i can get the information off of ubuntu and onto here without hand writing it?

---

### Post by Slushdoot on 2008-03-31
lspci > lspci.txt
That will direct the output of lspci to a text file in your home directory called lspci.txt.  Put this on a disk (USB flash is just about perfect) and walk it over to a machine with Internet access. :)

---

### Post by HeadLikeAHole531 on 2008-03-31
i just got that info saved, now im just logging back onto xp to open it and send it, should be within a minute or 2

---

### Post by HeadLikeAHole531 on 2008-03-31
okay, i saved it as a text document directly to my xp's desktop folder while i was on ubuntu, but i cant open it in xp. i was a little confused with your directions, and i dont have a flash drive so i cant do that. :(

---

### Post by HeadLikeAHole531 on 2008-03-31
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
dan@Home:~$

---

### Post by Slushdoot on 2008-03-31
Ok, it looks like your adapter is a Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Looking at this thread: [http://ubuntuforums.org/showthread.php?t=607953](http://ubuntuforums.org/showthread.php?t=607953)
signs are not good.  They were unable to get it working, perhaps because of a kernel problem.

On the somewhat positive side, wired Ethernet cards are dirt cheap.  If most computer enthusiasts are like me they've got a box in the cellar with a dozen old PCI cards.  As around and see if you know somebody who's got one.

Failing all else I might be able to post you one of my spares provided you're in the contiguous U.S.

---

### Post by HeadLikeAHole531 on 2008-03-31
thanks a lot for your help. i have another ethernet card actually, i tryed it earlier but i didnt quite know what to do with it, its a linksys LNE100TX.

---

