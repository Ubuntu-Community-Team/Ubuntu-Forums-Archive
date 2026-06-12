---
title: "Programs crash randomly in Edgy..."
date: 2006-11-15
forum: General Help
---

### Post by Contrast on 2006-11-15
I've given Edgy a few tries so far, twice each on my desktop (1GB RAM, 200GB HD, 3.4 Pentium 4) and laptop (512MB RAM, 30GB HD, 2,4 Pentium 4). There are a few things in it that I really like, but none of them are outweighed by this problem that keeps coming up. I'll be in the middle of using a program (Adept, Firefox, XMMS, etc. - all programs that were installed from the repositories), and without warning, the program "kills" itself. Its window disappears from my screen, and there's no trace of it in the task manager. It appears to be random, as performing certain functions within the programs don't duplicate the problem. I get this with both fresh installs and upgrades. This has happened on Dapper as well, but I could count on one hand how many times over the course of a couple months, while it's happened well over twice as many times in less than half the time with Edgy. As you can imagine, this can be extremely frustrating, and as of now, it's the only thing holding me back from upgrading to Edgy. I'd like to give the latest Ubuntu release one more chance before completely giving up on it. I'm willing to use my laptop as a test bed if anyone can offer any solid advice. I looked through the "Known bugs and workarounds for Edgy" thread and didn't see this mentioned anywhere. If anyone can help me with this, or simply point me in the direction where I can find out if/when this bug has been fixed, it would be greatly appreciated.

---

### Post by ashmew2 on 2006-11-18
Im having the same problem , programs keep crashing randomly and sometimes disappear without any warning. The system hangs frequently too. Im using the Gnome Desktop on Edgy Eft. Please help.

---

### Post by RFScheer on 2006-11-18
Edgy has been very stable in several incarnations on my machine.  I've been poking around trying various installs and customizations.  The only thing like your problem I've seen is after trying to upgrade from 32b to 64b.  

A clean install was all it took to avoid this.

Please describe how you did your install and whether you're preserving partitions such as /home or /usr between different installs.

---

### Post by Contrast on 2006-11-18
I did a clean install twice, and an upgrade from Dapper twice (using the exact instructions on the [http://kubuntu.org/announcements/6.10-release.php]("Kubuntu Edgy homepage")). On the clean installs, I completely formatted my hard drive, not preserving anything from my previous Dapper installation.
All four of these installs (both methods performed on both my desktop and laptop) gave the same results regarding program instability.

---

### Post by shootonj on 2007-03-21
First I would like to say I love Ubuntu it has made the switch from Windows so easy. I have searched the forms and looked for the answer to my question but am unable to find it. I wonder if someone might be able to help.

I installed a clean install of Ubuntu (a few times actually) and it is fantastic to begin with but after updating programs close without warning and at random intervals. At first I just thought it was firefox and therefore switched browsers but Opera does the same, and now Open Office is having the same problems. 

Can anyone offer an explanation or even better a solution.

---

### Post by automatthias on 2007-03-25
I have a similar problem on a Sony VAIO laptop with Edgy Eft (installed from scratch, not upgraded from Dapper). My laptop has Core Duo (32-bit), 1 GB of memory and Intel integrated graphic card:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 13)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments Unknown device 8039
08:03.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
08:03.2 Mass storage controller: Texas Instruments Unknown device 803b

```

It's all programs that crash: Most commonly it's Firefox, which crashes about 10 times a day. Other crashing applications include Eclipse (which I'm using a lot), gnome-terminal and gkrellm. I have never seen gnome-terminal or gkrellm crashing like that. I also had Firefox uptimes for at least 24h.

I suspect that it's got something to do with the X server, but I don't know how to diagnose it.

---

