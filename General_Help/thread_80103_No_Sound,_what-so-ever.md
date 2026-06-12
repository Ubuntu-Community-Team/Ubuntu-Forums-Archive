---
title: "No Sound, what-so-ever"
date: 2005-10-21
forum: General Help
---

### Post by fezith on 2005-10-21
Hi there.

I'm relitively new to Ubuntu, and Linux in general.  I think I need drivers for my soundcard, as linux plays NO sound.  After researching the best I could, I found out that I should check if it detects my soundcard at all in the Device Manager.  I went to System > Administration > Device Manager and it says the following:

Vender: Intel Corp.
Device: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

Anyone who can help me find the correct drivers, I'll be forever thankful!  Oh, I am using a Gateway Laptop (Model 4530GZ).

---

### Post by Kyral on 2005-10-21
hmm..

type lspci at the command line and paste the output please.

---

### Post by objorkum on 2005-10-21
Don't care about lspci yet.

Type "alsamixer" in a terminal.

Du you get the volume controls? Check that Master and PCM are not "Off" (turn on with M), and that the volume are on.

---

### Post by Kyral on 2005-10-21
I was trying to find out if ALSA supported his card and I needed the chipset ;P

---

### Post by shensi on 2005-10-21
Hi everybody!  :confused: :confused: :confused: 

i installed Ubuntu 2 weeks ago and i didn't find out how to hear a music from this system.
i 've got a sound blaster platinum
 I went to System > Administration > Device Manager and it looks likemy settings are good.

someone told me something like: db packaging or something so if you can sort out this **** 
thanks for everyone
cheers

---

### Post by Kyral on 2005-10-21
Try this
[https://wiki.ubuntu.com/SoundProblemsHoary](https://wiki.ubuntu.com/SoundProblemsHoary)

---

### Post by shensi on 2005-10-21
ubuntu recognizes my device 

i use VLC player...it can read my music

with the Totem driver is telling me:
There were no decoders found to handle the stream, you might need to install the corresponding plugins

:(

---

### Post by Kyral on 2005-10-21
Ah! Thats a different problem altogether!

[https://wiki.ubuntu.com/RestrictedFormats#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8](https://wiki.ubuntu.com/RestrictedFormats#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8)

---

### Post by fezith on 2005-10-25
okay...made sure everything was unmuted in "alsamixer" and that worked okay.  But, still no sound.  The lspci output was:

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

I hope this makes sense to you.  I didn't reply sooner because I was fighting with windows xp which obviously likes to write over the MBR, without asking anyone.  That problem was all resolved, but the sound issue is all I have left to figure out!

Thanks!

---

### Post by fezith on 2005-10-30
bump...anyone?  pleassse?

---

