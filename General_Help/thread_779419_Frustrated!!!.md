---
title: "Frustrated!!!"
date: 2008-05-02
forum: General Help
---

### Post by CheeseQueen452 on 2008-05-02
Ok, I just installed a fresh copy of Ubuntu 8.04, & I STILL have a sound issue. My startup, shutdown, & email sounds don't work. I'm really frustrated!! I even tried Xubuntu, & there wasn't any sound AT ALL. This is driving me crazy!! If anyone can help, I'd appreciate it!!

---

### Post by TeoBigusGeekus on 2008-05-02
Please post the output of 
```
lspci
```

---

### Post by CheeseQueen452 on 2008-05-02
> **TeoBigusGeekus said:**
> Please post the output of 
```
lspci
```

00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:02.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
03:04.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
03:04.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)

---

### Post by TeoBigusGeekus on 2008-05-02
Have a look at this
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=480791]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=480791")

---

### Post by CheeseQueen452 on 2008-05-02
How is that supposed to help me? I don't have 2 sound cards, & the sounds DID work before I upgraded to 8.04.

> **TeoBigusGeekus said:**
> Have a look at this
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=480791]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=480791")

---

### Post by Jammerdelray on 2008-05-02
Have you tried downloading the linux sound driver from your sound card manufacturer?

---

### Post by TeoBigusGeekus on 2008-05-02
The guy's sounds did work before he upgraded and he had the same problem with you: couldn't get his second sound card to work(Creative Labs SB Live! EMU10k1), just his on board one.
Anyway... it was just a suggestion! Sorry for wasting your time...

---

### Post by CheeseQueen452 on 2008-05-02
No, I don't know where to find it.

> **Jammerdelray said:**
> Have you tried downloading the linux sound driver from your sound card manufacturer?

---

### Post by TeoBigusGeekus on 2008-05-02
Manufacturer's site perhaps?

---

### Post by CheeseQueen452 on 2008-05-02
I don't know what the company name is, but I'll look into it. Not that I expect anything to come of it....

> **TeoBigusGeekus said:**
> Manufacturer's site perhaps?

---

### Post by TeoBigusGeekus on 2008-05-02
[http://gr.europe.creative.com/support/downloads/]("http://gr.europe.creative.com/support/downloads/")

---

### Post by TeoBigusGeekus on 2008-05-02
Ignore my last post. I've found something better.
[http://sourceforge.net/projects/emu10k1/]("http://sourceforge.net/projects/emu10k1/")

---

### Post by CheeseQueen452 on 2008-05-02
Where do I extract the files to, once I download it?

> **TeoBigusGeekus said:**
> Ignore my last post. I've found something better.
[http://sourceforge.net/projects/emu10k1/]("http://sourceforge.net/projects/emu10k1/")

---

### Post by TeoBigusGeekus on 2008-05-02
Home folder or Desktop should be fine.

---

### Post by CheeseQueen452 on 2008-05-03
Huh? That doesn't make sense.... how is the system supposed to know that the driver is there?

> **TeoBigusGeekus said:**
> Home folder or Desktop should be fine.

---

### Post by Canis familiaris on 2008-05-03
You first have to extract it!
Copy the archive to home folder.
Open Terminal. (Applications->Accessories->Terminal)
type:
```
tar xvzf <name of archive>.tar.gz
cd <name of archive>

```
Read the instruction or post the output of ls here:
```
ls -al
```

---

### Post by CheeseQueen452 on 2008-05-03
The file I downloaded is a tar.bz2. When I tried to open it in the terminal, it said "access denied". I have no clue what to do.

> **Anurag_panda said:**
> You first have to extract it!
Copy the archive to home folder.
Open Terminal. (Applications->Accessories->Terminal)
type:
```
tar xvzf <name of archive>.tar.gz
cd <name of archive>

```
Read the instruction or post the output of ls here:
```
ls -al
```

---

### Post by CheeseQueen452 on 2008-05-04
Well, if anyone can help me I'd appreciate it! I installed a few things for ALSA via Synaptic, but to no avail. If there's a package I can install that'll do the trick, PLEASE clue me in!!

---

### Post by jimv on 2008-05-04
Try going into the Sound control panel and set the first pull-down menu to ALSA.  Then click Test and see if you get any sound.

---

### Post by CheeseQueen452 on 2008-05-04
I already tried that.

> **jimv said:**
> Try going into the Sound control panel and set the first pull-down menu to ALSA.  Then click Test and see if you get any sound.

---

### Post by jimv on 2008-05-04
That's so odd.  The only difference between sound in Gutsy and sound in Hardy that I know of is that Hardy uses PulseAudio.

I did read something the other day about some people's audio coming through the wrong channel...like one guy's mic volume was actually controlling his speaker volume, and his speaker volume was controlling his left/right channel balance.  Maybe something like that is happening on yours?

---

### Post by IcemanV9 on 2008-05-04
It had happened to me when I installed Edubuntu on HP laptop past weekend for my kids to play and learn. No sound! I found out it was unmuted in all except Master. So, type in your terminal ...
```
alsamixer
```
then, unmute one device at a time or all. And, test it.

---

### Post by CheeseQueen452 on 2008-05-05
I don't think that's the case.... But how do I find out?

> **jimv said:**
> That's so odd.  The only difference between sound in Gutsy and sound in Hardy that I know of is that Hardy uses PulseAudio.

I did read something the other day about some people's audio coming through the wrong channel...like one guy's mic volume was actually controlling his speaker volume, and his speaker volume was controlling his left/right channel balance.  Maybe something like that is happening on yours?

---

### Post by CheeseQueen452 on 2008-05-05
No, nothing is muted.

> **IcemanV9 said:**
> It had happened to me when I installed Edubuntu on HP laptop past weekend for my kids to play and learn. No sound! I found out it was unmuted in all except Master. So, type in your terminal ...
```
alsamixer
```
then, unmute one device at a time or all. And, test it.

---

