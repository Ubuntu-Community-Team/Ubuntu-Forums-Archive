---
title: "Can't read Cds"
date: 2007-03-25
forum: General Help
---

### Post by cactaur on 2007-03-25
I've recently come across a really weird problem. Whenever I put in a CD or DVD into my drive, Ubuntu does not auto-open my CD files, and when I try to see it in nautilus, I get a 
```
Unable to mount the selected volume
mount: must be superuser to use mount
```
I think this happened after I used graveman to burn a DVD that I didn't finalize. I'm not sure if that caused the problem, but it is a rather amazing coincidence. When I do
```
sudo nautilus
```
I can't find the CD/DVD drive, when I look in /media/cdrom0, the folder is empty. I've tried to use different CDs and DVDs, but it's still plaguing me, any help?

---

### Post by tgalati4 on 2007-03-25
Sometimes the automounter takes a while to discover the disk.  Try a fresh boot, put in a disk, and then wait a few minutes to see if it gets picked up automatically.  If you go into nautilus before the automounter finds it, you will get a similar error.

Examine your /etc/fstab.  You should have a similar entry:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Reboot with a live CD.  Go to "options" and run a CD check.  This will read the entire disk.  If you have a wonky drive, this will show it.

Good luck.

---

### Post by cactaur on 2007-03-26
Nope, still no response from Ubuntu.

My fstab looks ok, this is he CDROM line:

```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I ran the check, and everything went by smoothly. I think this means that it has something to do with the software. Not a hardware bug.

---

### Post by dcstar on 2007-03-26
> **cactaur said:**
> I've recently come across a really weird problem. Whenever I put in a CD or DVD into my drive, Ubuntu does not auto-open my CD files, and when I try to see it in nautilus, I get a 
```
Unable to mount the selected volume
mount: must be superuser to use mount
```
I think this happened after I used graveman to burn a DVD that I didn't finalize. I'm not sure if that caused the problem, but it is a rather amazing coincidence. When I do
```
sudo nautilus
```
I can't find the CD/DVD drive, when I look in /media/cdrom0, the folder is empty. I've tried to use different CDs and DVDs, but it's still plaguing me, any help?

Look at the output of:
```
dmesg
``` when you insert a CD and post the last lines here for analysis.

---

### Post by cactaur on 2007-03-26
> Look at the output of:
Code:

dmesg

when you insert a CD and post the last lines here for analysis.

There doesn't seem to be any log output on dmesg. These are the last 10 lines on dmesg before I put the CD in:

```
[17179619.112000] Bluetooth: Core ver 2.8
[17179619.112000] NET: Registered protocol family 31
[17179619.112000] Bluetooth: HCI device and connection manager initialized
[17179619.112000] Bluetooth: HCI socket layer initialized
[17179619.328000] Bluetooth: L2CAP ver 2.8
[17179619.328000] Bluetooth: L2CAP socket layer initialized
[17179619.340000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179619.396000] Bluetooth: RFCOMM socket layer initialized
[17179619.396000] Bluetooth: RFCOMM TTY layer initialized
[17179619.396000] Bluetooth: RFCOMM ver 1.7

```

And these are the last 10 after:

```
[17179619.112000] Bluetooth: Core ver 2.8
[17179619.112000] NET: Registered protocol family 31
[17179619.112000] Bluetooth: HCI device and connection manager initialized
[17179619.112000] Bluetooth: HCI socket layer initialized
[17179619.328000] Bluetooth: L2CAP ver 2.8
[17179619.328000] Bluetooth: L2CAP socket layer initialized
[17179619.340000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179619.396000] Bluetooth: RFCOMM socket layer initialized
[17179619.396000] Bluetooth: RFCOMM TTY layer initialized
[17179619.396000] Bluetooth: RFCOMM ver 1.7

```

There is no change.

---

### Post by dcstar on 2007-03-26
> **cactaur said:**
> There doesn't seem to be any log output on dmesg. These are the last 10 lines on dmesg before I put the CD in:
........
There is no change.

Well, it looks like Ubuntu is not seeing the hardware at all.

You may have a bad CD drive or cable, check that it is detected in your BIOS.

---

### Post by tgalati4 on 2007-03-26
Did you add any hardware recently?  Perhaps there is a DMA or interrupt conflict?

post:

lspci -vv

/proc/interrupts

In BIOS, turn off serial, USB, and parallel ports (temporarily).  Reboot and see if the drive is recognized.

---

### Post by cactaur on 2007-03-26
There is no new hardware. As I said, my CD drive worked fine before I used Graveman. In fact, when I inserted the DVD to burn in Graveman, it worked, but afterward, it didn't. I'm starting to think graveman had something to do with this.

Ubuntu detects the hardware. When there's no cd in the drive, the CD-RW/DVD+-R is not there, but when I insert a CD, it comes up. However, when I try to get into the CD, it brings up the mount error.

And here is my lspci -vv:

```
gregory@gregory-desktop:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: d0000000-efffffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 177
        Region 4: I/O ports at cc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 185
        Region 4: I/O ports at c000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 169
        Region 4: I/O ports at c400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 177
        Region 4: I/O ports at c800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 193
        Region 0: Memory at fa100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fa000000-fa0fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 169
        Region 0: I/O ports at <unassigned>
        Region 1: I/O ports at <unassigned>
        Region 2: I/O ports at <unassigned>
        Region 3: I/O ports at <unassigned>
        Region 4: I/O ports at f000 [size=16]
        Region 5: Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 5
        Region 4: I/O ports at 0500 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Elitegroup Computer Systems Unknown device 1875
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 201
        Region 0: I/O ports at d400 [size=256]
        Region 1: I/O ports at d800 [size=64]
        Region 2: Memory at fa101000 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at fa102000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550] (prog-if 00 [VGA])
        Subsystem: PC Partner Limited Unknown device 0200
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 255 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 177
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Region 1: I/O ports at a000 [size=256]
        Region 2: Memory at f9000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at f8000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
        Subsystem: PC Partner Limited Unknown device 0201
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: Memory at e0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Region 1: Memory at f9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

02:01.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-Link AirPlus DWL-G520 Wireless PCI Adapter(rev.B)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 185
        Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

And /proc/interrupts doesn't exist on my machine.
And the problem still exists after disabling parallel, serial, and usb ports.

I'll start looking at graveman to see if it could've caused this problem. However, if anyone has any other ideas, please do tell. I'm getting rather despsarate.

---

### Post by tgalati4 on 2007-03-26
Is it as simple as a permissions problem? Check in /dev:

 ls -la cd*

lrwxrwxrwx 1 root root 3 2007-03-25 11:57 cdrom -> hdc

ls -la dv*
lrwxrwxrwx 1 root root 3 2007-03-25 11:57 dvd -> hdc

---

### Post by cactaur on 2007-03-26
Hmmmm.....that's a good idea.

Dang, it's not the problem:

```
gregory@gregory-desktop:/dev$ ls -la cd*
lrwxrwxrwx 1 root root 3 2007-03-26 16:39 cdrom -> hdc
lrwxrwxrwx 1 root root 3 2007-03-26 16:39 cdrw -> hdc
gregory@gregory-desktop:/dev$ ls -la dv*
lrwxrwxrwx 1 root root 3 2007-03-26 16:39 dvd -> hdc
lrwxrwxrwx 1 root root 3 2007-03-26 16:39 dvdrw -> hdc

```

This is like some sort of a puzzle that's really hard to solve. I can't believe it!

---

### Post by tgalati4 on 2007-03-27
Here's another reach:

Perhaps graveman does some low-level access directly with the drives.  Perhaps these controller bits get set and remain set until complete power off.  Have you tried unplugging power from the drives themselves and replugging and rebooting?

I have always used K3B with good CD and DVD burn results.  I don't have any experience with graveman.

It's also possible that the firmware in the drives is messed up.  Perhaps reloading or upgrading the firmware in the drives will restore them.

If these are Sony drives, I know that they have some copy protection built into the drives.  It would not surprise me if this copy protection includes shutting the drives down if certain conditions exist.

---

### Post by cactaur on 2007-03-27
Unfortunately, that didn't work either.

But I did come up with something. I did the obvious:

```
sudo mount /dev/hdc
```

That mounts the CDROM drive, and it worked. Perhaps that could also be a hint. Because I don't wanna mount the CD-drive every time I need to use it.

---

### Post by tgalati4 on 2007-03-27
Maybe it is as simple as graveman taking control of the drive, perhaps unmounting it then remounting it with different owners/permissions.  This might prevent other processes from messing up a burn.  When you exit the program, the drives remain unmounted.

If this is the case, then you could write a script to remount the drive after digging with graveman.  Do you get the same behavior running K3B or Serpentine?

If the behavior is consistent with graveman only, then it's time to elevate the issue to the graveman developer site.

Another possibility is that graveman does something with locking the device and the kernel responds by unmounting it automatically to keep the system up.  You have to love that.

---

### Post by cactaur on 2007-03-27
Nope, every burn I did before graveman turned out great (and I burned a lot of CDs). I set up a bug report on the graveman web site, and maybe I should ask on their mailing list because this could be a very serious problem and needs attention. Since I figured out a band-aid solution, I think I'll try to get an answer out of there, and thank you very very much tgalati4. I don't know where I'd be without your help.

---

### Post by tgalati4 on 2007-03-27
You're welcome.  Let us know what finally works for you.

How is graveman different from Serpentine or K3B?  Why should I use it?

---

### Post by cactaur on 2007-03-27
Well, I basically needed a program to make a multisession DVD. I didn't feel like installing the KDE packages in Ubuntu, so I didn't use K3b. Serpentine didn't have the capability to burn data to a CD, so I heard about Graveman. But now I know to just install the KDE files and use K3b

---

### Post by tgalati4 on 2007-03-27
Be sure to turn your stereo down if it's hooked up to your computer.  When K3b finishes a burn, you get a loud trumpet!

The advantage of having KDE libraries is that you can try the cool KDE applications.  Some of them are excellent.  Others are good but will crash sometimes.  That is why I went from Kubuntu back to Dapper Ubuntu.  I got tired of application crashes.  Perhaps it's better now, but I am waiting for KDE 4.0 to come out (as is everyone else).

---

