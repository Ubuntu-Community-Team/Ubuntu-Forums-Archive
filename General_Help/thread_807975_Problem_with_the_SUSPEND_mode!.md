---
title: "Problem with the SUSPEND mode!"
date: 2008-05-26
forum: General Help
---

### Post by rakan_dr on 2008-05-26
hi guys,
I have problem with Ubuntu which is the Suspend mode.
When I click on in the computer goes to Sleep but after 1 second or less it goes back to normal state!!!

I have windows and the Stand By works great, but I don't know what's the problem with Ubuntu.

These are my Computer specifications:
CPU: INTEL P4 3.60GHz 
Motherboard: ASUS P5GZ-MX, built-in Video Card!! very bad 64MB VRAM.
RAM: 2GB
H.D: 160 WD

So how can I solve it?

---

### Post by rakan_dr on 2008-05-26
Hello guys! anybody?...

---

### Post by rakan_dr on 2008-05-26
nobody faced this problem before???

---

### Post by m i k e on 2008-05-26
I have the same issue.  I'm guessing it has to do with video card drivers (I have an ATI Radeon 9800 Pro) but I'm not sure.  I've been posting about it as well and haven't found an answer.  Help anyone?

---

### Post by rakan_dr on 2008-05-26
Thanks god, someone supports me!!!!

---

### Post by rakan_dr on 2008-05-27
Hey! where are the geeks!

---

### Post by danwood76 on 2008-05-27
What drivers are you using to drive the video card, and what card is it?
Also what kernel version are you running?

---

### Post by rakan_dr on 2008-05-27
> **danwood76 said:**
> What drivers are you using to drive the video card, and what card is it?
Also what kernel version are you running?

I'm using Ubuntu 8.04.

This is the name of my integrated video adapter with the version of the driver:

Intel(R) 82945G Express Chipset Family
Driver Provider: Intel Corporation
Driver Date: 3/23/2006
Driver Version: 6.14.10.4543

I hope you could help me.:)

---

### Post by danwood76 on 2008-05-27
Well Intel qraphics drivers tend to be quite good, I doubt they would be causing you issues.
There is a resume bug in the latest ubuntu kernel update but this effects the resume from suspend so I doubt its the same issue.

---

### Post by rakan_dr on 2008-05-27
So now the problem is in Ubuntu not in my Hardware???

---

### Post by Maratonda on 2008-05-29
I guess it's the kernel?

[https://bugs.launchpad.net/ubuntu/+bug/226279](https://bugs.launchpad.net/ubuntu/+bug/226279)

---

### Post by danwood76 on 2008-05-29
Your issue does seem different to the kernel bug.
(thats a dupe of the bug I was speaking of)

Can you give us a full run down of your hardware?

```

lspci

```
Where did you get that driver info from in one of your previous posts?

---

### Post by m i k e on 2008-05-29
I don't mean to steal this thread but I as stated before, I have the same issue.  Right now I have disabled the ATI proprietary driver but am still getting the same suspend issue.  This leads me to believe, like one of you said, that it might be a kernel issue.  I did however have the exact same problem with Gutsy before the upgrade.  I typed in "lspci" and got:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
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
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
02:04.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:0b.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
```

Any help would be greatly appreciated.

---

### Post by fjgaude on 2008-05-29
My experience with Suspend and recovery all has to do the motherboard, its BIOS, and who made them.

The Linux folks simply can't get it all right because there is so much variations and many of the suppliers don't give the details of their hardware. It's something we have been living with since 1992. It's still a Windows Microsoft world.

---

### Post by m i k e on 2008-05-29
I have a pretty generic ASUS mobo though.  I'd think I should be able to get it to work.

---

### Post by rakan_dr on 2008-05-30
> **danwood76 said:**
> Your issue does seem different to the kernel bug.
(thats a dupe of the bug I was speaking of)

Can you give us a full run down of your hardware?

```

lspci

```
Where did you get that driver info from in one of your previous posts?

Hey man, I'm sorry but I got those info from Windows!!!:confused: "Stupid I know!".
Anyway I got this info now from Ubuntu:
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

01:00.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 01)

01:01.0 Communication controller: Agere Systems Unknown device 0620

01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
```

I hope also if anyone can help me with the modem.

---

### Post by rakan_dr on 2008-06-02
hello anybody??!

---

### Post by danwood76 on 2008-06-03
Can you post the contents of your xorg.conf so we can see which drivers are being used?

The following command will dump it to the terminal:
```

cat /etc/X11/xorg.conf

```

---

### Post by eAspenwood on 2010-11-29
I resolved this issue today by putting the USB jumpers on positions 2 and 3.

I have the same P5GZ-MX board and am running ubuntu desktop 10.10.

You can download the user manual from the Asus website to see where on the board the jumpers are located.

-- J.

---

### Post by danwood76 on 2010-11-30
@eAspenwood

This means that one of your USB devices is causing the issue.
Setting those USB jumpers means that in suspend (and hibernate/off) the USB ports are left unpowered.

This causes your USB devices to re instantiate on power up.

---

