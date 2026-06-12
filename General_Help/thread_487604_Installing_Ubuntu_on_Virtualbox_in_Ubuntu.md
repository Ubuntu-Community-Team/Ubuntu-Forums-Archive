---
title: "Installing Ubuntu on Virtualbox in Ubuntu"
date: 2007-06-29
forum: General Help
---

### Post by Ebuntor on 2007-06-29
Hi everyone,

I needed to make several screenshots of a standard Ubuntu Feisty install. I didn't want reboot to load a LiveCD session every time so I wanted to try it in Virtualbox.

I first used a Feisty Shipit CD. The problem is that when I start it up the I get the menu if I want to start the LiveCD session or do a HDD boot. I choose the LiveCD session and I get a black screen. Normally I should get a whole list of drivers being loaded but nothing happens.

I tried it with my Shipit CD, a Desktop CD iso and an iso of the alternate install CD. I get the same problem with all of them yet Windows XP, Slax and DSL work perfectly from a CD and iso.

Any ideas?

---

### Post by Ebuntor on 2007-07-01
*bump*

Can anyone help me? 

Thanks in advance

---

### Post by zach12 on 2007-07-01
get the .iso file(of ubuntu)and then set vbox to boot from the iso

---

### Post by Ebuntor on 2007-07-01
> **zach12 said:**
> get the .iso file(of ubuntu)and then set vbox to boot from the iso

Thanks, but I already tried that as mentioned in my original post.

---

### Post by zach12 on 2007-07-01
odd go to the vbox website

---

### Post by vinfred on 2007-07-05
I have exactly the same problem.
I'm running Ubuntu Feisty (generic kernel) and I wanted to give a try to Xubuntu and Kubuntu in a VM. I installed VirtualBox from the depots, using Synaptics.
"http://www.virtualbox.org/debian feisty non-free"
and I downloaded the .iso files from the official Ubuntu sites.
I have the same problem on either of these distros.

The VM starts booting, I can change the language (I'm French), keyboard, start options ...
but as soon as starting the system itself, the VM Hangs. 
Restarting the VM gets the same result.

Looking in the VM log  .VirtualBox/Machines/Xubuntu/Logs, I find the following:

```

...
00:00:30.351 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:30.364 Guest Log: BIOS: VirtualBox 1.4.0
00:00:30.365 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:30.383 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:30.399 Display::handleDisplayResize(): pvVRAM=b2816000 w=640 h=480 bpp=8 cbLine=0x280
00:00:32.743 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:32.743 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:32.744 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:32.745 Guest Log: BIOS: ata0-0: PCHS=16253/16/63 translation=lba LCHS=1019/255/63
00:00:32.746 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:32.746 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:32.747 Display::handleDisplayResize(): pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:32.750 Guest Log: BIOS: Booting from Hard Disk...
00:00:34.391 Display::handleDisplayResize(): pvVRAM=b2816000 w=640 h=480 bpp=16 cbLine=0x500
00:01:43.426 PIIX3 ATA: LUN#2: CD-ROM block number 282640 invalid (READ)
00:01:43.426 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:01:43.427 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
...

```

and several Mio of the last message, until I stop the VM.

I'm pretty certain I could burn any of these CD and install it on a physical machine.
Any idea ?

Vinfred

---

### Post by Bd0g on 2007-07-05
[http://forums.virtualbox.org/viewtopic.php?t=657&highlight=ubuntu]("http://forums.virtualbox.org/viewtopic.php?t=657&highlight=ubuntu")

Doing as the last guy in that thread and increasing to 512mb for the guest os might work.

I've also experienced this issue (ubuntu & mint).. but I cant try his example unfortunatly.

---

### Post by Ebuntor on 2007-07-05
> **Bd0g said:**
> [http://forums.virtualbox.org/viewtopic.php?t=657&highlight=ubuntu](http://forums.virtualbox.org/viewtopic.php?t=657&highlight=ubuntu)

Doing as the last guy in that thread and increasing to 512mb for the guest os might work.

I've also experienced this issue (ubuntu & mint).. but I cant try his example unfortunatly.

Thanks, I tried it with a LiveCD and an ISO, didn't work. :(

---

### Post by vinfred on 2007-07-05
I made another test.
I used an Ubuntu 7.04 CD which I did use to install Ubuntu, and therefore is known to work.
I tried to start the VM.
The live CD had a problem when loading GNOME (I have only declared 128Mb for the VM and 4Mb for the video) but at least, the boot sequence started quite well.

Then I decided to make an .iso from the CD, using 
> 
dd -if=/dev/cdrom -of=ubuntu-7.04-desktop-i386.iso


And started again the VM using this newly created .iso image instead of the actual CD.
Beng! same error!

> 
00:00:08.577 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:08.577 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:08.610 Guest Log: BIOS: VirtualBox 1.4.0
00:00:08.610 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:08.655 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:08.663 Display::handleDisplayResize(): pvVRAM=b293b000 w=640 h=480 bpp=8 cbLine=0x280
00:00:10.992 Display::handleDisplayResize(): pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:10.994 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:10.996 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:10.997 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:10.999 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 translation=lba LCHS=1024/255/63
00:00:11.000 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:11.000 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:11.004 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:11.046 Guest Log: BIOS: Booting from Hard Disk...
00:00:13.437 Display::handleDisplayResize(): pvVRAM=b293b000 w=640 h=480 bpp=16 cbLine=0x500
00:00:45.803 PIIX3 ATA: LUN#2: CD-ROM block number 328192 invalid (READ)
00:00:45.803 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.804 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.805 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.806 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.807 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.808 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.808 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.809 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.810 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
00:00:45.811 Guest Log: BIOS: int13_cdrom: function 42, status 04 !
....



I guess VirtualBox doesn't handle correctly such linux .iso images, or there is a trick to make it work.

The machine on which I made this test is so small that I cannot increase the memory for the VM (I only have 256Mb physical memory on the host!). I'll try the same test on a bigger machine later.

---

### Post by Ebuntor on 2007-07-11
> **vinfred said:**
> I made another test.
I guess VirtualBox doesn't handle correctly such linux .iso images, or there is a trick to make it work.


I agree, it seems Kubuntu and Xubuntu have the same problem. It has to do with the liveCD. However 6.10 Edgy Eft does work. 

It's pretty funny actually, nearly every OS can run on Virualbox even the most primitive Linux distros but Ubuntu can't.

If anyone knows a fix for this I'd much appreciate it. :)

---

### Post by zach12 on 2007-07-11
hey i tryed vbox and xubuntu iso works fine

---

### Post by Ebuntor on 2007-07-12
> **zach12 said:**
> hey i tryed vbox and xubuntu iso works fine

Did you use the latest version 7.04 Feisty Fawn? Edgy and Dapper work fine.

---

### Post by smoker on 2007-07-12
i've had no problems installing iso images of both xubuntu, mint, and ubuntu, in virtualbox, but i had allocated plenty memory and graphics for the purpose (512 & 128 respectively, if i remember).

---

### Post by Ebuntor on 2007-07-12
> **smoker said:**
> i've had no problems installing iso images of both xubuntu, mint, and ubuntu, in virtualbox, but i had allocated plenty memory and graphics for the purpose (512 & 128 respectively, if i remember).

Thanks I tried it those memory and graphic settings. However as has been posted earlier it almost certainly only has to do with the Live CD not booting the kernel not the base and/or graphics memory.

Just to be certain when installing (X)Ubuntu you are talking about Feisty?

---

### Post by smoker on 2007-07-12
yes, i was talking about feisty, though i did not burn the iso's to disk, just mounted as iso's in the cd drive section.

---

