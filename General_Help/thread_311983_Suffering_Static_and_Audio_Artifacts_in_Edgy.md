---
title: "Suffering Static and Audio Artifacts in Edgy"
date: 2006-12-03
forum: General Help
---

### Post by SavantEdge on 2006-12-03
The Problem:
Ever since I upgraded to Edgy, whenever I try to play music, the sound comes out distorted, with a lot of static in particular.

Details and Results of my own troubleshooting:
[LIST]
[*]Only happens in Linux, not in Windows (same computer, dual boot).
[*]Did not happen in Dapper Drake, only in Edgy Eft (did not upgrade existing install, did a clean reformat-install).
[*]Happens both with normal speakers, external speakers, and 3 different sets of headphones.
[*]Happens in Totem, Amarok, XMMS.
[*]Happens when listening to most streams, as well as almost all music off the HDD in MP3 and M4A formats (it is most audible in the bass, but sometimes also in treble).
[*]I have tried every option on the Sounds Preferences dialog, including two different Intel 82801DB-ICH4 entries, ALSA, OSS, and ESD.
[/LIST]

Below is the output of lspci (if it helps):
```
neil@ion:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
```

Any other information that would help this can be provided, just tell me what to do...

---

### Post by SavantEdge on 2006-12-04
No one has any ideas?

---

### Post by OsireS on 2006-12-13
I've been having the exact same issues (sound crackly and full of static in Linux and perfect in Windows). 

If you have found a solution or workaround I'd really appreciate it if you could let me know. I've tried installing the latest ALSA (compiling from source), using polysound .. and a number of other things with no success.

---

### Post by SavantEdge on 2006-12-13
My workaround?  Do everything except my dev work in Windows so I can listen to music while I do it.  Then switch to Linux for the dev, and use an mp3 player for music.  Not a happy solution. :mad:

---

### Post by midtown on 2007-09-08
I am having this same problem after installing Gutsy Tribe 5 with my USB soundcard, which worked fine in Feisty.

Not really sure what to do!

In RhythmBox, making the volume anything but 100% seems to fix the issue. Maybe my issue is just RhythmBox. Hmmm!

---

### Post by MicahCarrick on 2007-10-09
I'm experiencing the same problem. Upgraded from Feisty to Edgy and now the sound is crackly. Happens in speakers, headphones, etc. Worked fine prior to upgrade, works fine in FC6 installation on same box.

---

### Post by MicahCarrick on 2007-10-09
This appears to be quite common. As a temporary fix, enable the crossfading backend in Rythmbox:

Edit > Preferences. Playback tab. Check 'Use crossfading backend (requires restart)

The bug is detailed here: [http://bugzilla.gnome.org/show_bug.cgi?id=436192]("http://bugzilla.gnome.org/show_bug.cgi?id=436192")

---

