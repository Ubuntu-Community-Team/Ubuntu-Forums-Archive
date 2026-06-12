---
title: "SiS191 ethernet adapter problem in Hardy Heron 8.04"
date: 2008-06-15
forum: General Help
---

### Post by paul_atreides on 2008-06-15
:confused:Hello guys I need help fast. I just installed Hardy Heron 8.04 on my pc. My PC has a P5SD2-VM motherboard with built-in SiS191 ethernet adapter. The installation finish fine without errors or anything. Then i found out that there is not network connection. I can access network tool and settings. I set it to DHCP and configure it manually still won't work. I'm 100% sure there is nothing wrong with my network because I installed it dual boot and the network work perfectly in XP. When I try to configure eth0 in devices-network tool a prompt tells me that the device does not exist. Anyone have the same problem? Help will be very much appreciated. Thanks!

---

### Post by prince_niceguy on 2008-06-16
seems  your lan card is not having native linux drivers... you will have install ndiswrapper and then install windows driver to make it work...

---

### Post by paul_atreides on 2008-06-16
I think ndiswrapper only support wireless network card.

---

### Post by prince_niceguy on 2008-06-16
it works with lot of cards even lan cards, smart card etc... you can alwys give it a try.

---

### Post by paul_atreides on 2008-06-17
Thanks but having problem installing ndiswrapper in ubuntu. The tutorial is quite confusing :mad: Totally noob here

---

### Post by prince_niceguy on 2008-06-17
it is easy enough. before that can you put the output of following command

```
lspci
```

---

### Post by paul_atreides on 2008-06-17
Ok here what it says 

lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by prince_niceguy on 2008-06-17
OK... so here you go. I do not recall all the instructions as I had done this some couple of years back.

1. Get ndiswrapper installed. It is in the repository.
```
sudo apt-get install ndiswrapper
```

2. Now you need to get the drivers for the windows.
3. Install them for ubuntu.
```
sudo ndiswrapper -i <driver_from_windows>.inf
```

and hopefully it should be working now.

---

### Post by stell86 on 2008-06-24
Hi,
I've also have a P5SD2-VM-mb and have tried to install "ndsiwrapper" from the server-cd as well as the Alternate-cd, both 8.04.  There is nothing on there.
With no networkconnection, how do I get ndiswrapper on my system?

Thanks in advance....

---

### Post by prince_niceguy on 2008-06-24
It should be there. I see that you have spelt ndsiwrapper. actually it is ndiswrapper which needs to be installed. Can you recheck please. Also, enable multiverse and universe repos too.

---

### Post by stell86 on 2008-06-25
> **prince_niceguy said:**
> I see that you have spelt ndsiwrapper. actually it is ndiswrapper which needs to be installed.
Typo (blush) :)
> Also, enable multiverse and universe repos too.
Comment: With no working network connection (still trying to get LAN working), I disabled all repos except cd.  I also added 'alternate-cd' by "sudo apt-cdrom add"  (This is a server-install, not a normal desktop-install)

Enabling repos without any network connection does not make any sense - but I did check that.

OK, what I've done after a good night's sleep:
 - take HD and put into another machine that I know works - and booted from there to get network connection
 - Made sure all repos (not backport) are enabled
 - looked through some wiki's and how-to's and then tried to install "ndiswrapper-utils" - Apt complained that it is not available, but another package is: "ndiswrapper-common" - so I installed that.

I also went back to "Asus" website to see if they have anything for Linux - and lo and behold, under Downloads for the Mb they have an 'Other'-section, and there is a 15Mb zip file called "Linux-drivers".  Unfortunately it only has drivers for RedHat, FC6, Mandrive20 and Suse 10.1 (No Ubuntu :( ) (somebody should talk to them)
I have also downloaded their Lan-drivers for XP (32 bit) and looked into the zip-file for *.inf file (it seems only a 17 Kb - can this be right?).

Anyway - awaiting further instruction with anticipation.
Thanks for the help so far.


[EDIT:2008-07-02]
Just to finish off my post - I tried ndiswrapper and the driver, but couldn't get it to work - it showed up in "lspci" as "Gigabit Lan"  - anyway, I needed the server up and running for a client so I disabled on-board-lan and put a Dlink Gb-card in which was recognised immediatly.
So no more trying for me on this one for now - maybe later agian if I run into the MB again.
Thanks for the interest so far.
[/EDIT]

---

### Post by pusisaul on 2008-09-24
> **stell86 said:**
> Typo (blush) :)

Comment: With no working network connection (still trying to get LAN working), I disabled all repos except cd.  I also added 'alternate-cd' by "sudo apt-cdrom add"  (This is a server-install, not a normal desktop-install)

Enabling repos without any network connection does not make any sense - but I did check that.

OK, what I've done after a good night's sleep:
 - take HD and put into another machine that I know works - and booted from there to get network connection
 - Made sure all repos (not backport) are enabled
 - looked through some wiki's and how-to's and then tried to install "ndiswrapper-utils" - Apt complained that it is not available, but another package is: "ndiswrapper-common" - so I installed that.

I also went back to "Asus" website to see if they have anything for Linux - and lo and behold, under Downloads for the Mb they have an 'Other'-section, and there is a 15Mb zip file called "Linux-drivers".  Unfortunately it only has drivers for RedHat, FC6, Mandrive20 and Suse 10.1 (No Ubuntu :( ) (somebody should talk to them)
I have also downloaded their Lan-drivers for XP (32 bit) and looked into the zip-file for *.inf file (it seems only a 17 Kb - can this be right?).

Anyway - awaiting further instruction with anticipation.
Thanks for the help so far.


[EDIT:2008-07-02]
Just to finish off my post - I tried ndiswrapper and the driver, but couldn't get it to work - it showed up in "lspci" as "Gigabit Lan"  - anyway, I needed the server up and running for a client so I disabled on-board-lan and put a Dlink Gb-card in which was recognised immediatly.
So no more trying for me on this one for now - maybe later agian if I run into the MB again.
Thanks for the interest so far.
[/EDIT]

This is the problem with the SIS Gigabit ethernet drivers, see

[http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6)

---

### Post by mrincredible on 2008-10-19
:popcorn::popcorn::popcorn::popcorn:

Look here! All the previous posts are obsolete/for old versions. Don't run to ndiswrapper, don't waste your time.

[https://answers.launchpad.net/ubuntu/+question/38994](https://answers.launchpad.net/ubuntu/+question/38994)

You can either edit sis191.c, and recompile your kernel, as per above link, or wait a little longer... 2.6.28...29...ish kernels should have it patched...

:popcorn::popcorn::popcorn::popcorn:

---

### Post by johnnyxf on 2008-12-25
Greetings.

Trying to install Hardy Heron 8.04 on Novatech X15GS laptop, which has the SiS191 chip. Same problem: no network connection recognized.

The problem is not with the ISA bridge ID, according to dmesg, so I am trying the method suggested by john zhang, link in above post by mrincredible.

Indeed, as mrincredible suggests, the fix has been incorporated in kernel 2.6.28, exactly as in zhang's post.

However, I am stuck. I have the 2.6.28 source in /usr/src, and have tried to compile a new kernel module, sis190.ko, following instructions in [http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6]("http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6")
but all I get is a ream of error messages from
make oldconfig

Could someone explain exactly what I have to do to create this new module, please? I suspect that I have misinterpreted the instructions in the above link.

Incidentally, has this fix worked for anyone else?

---

### Post by prince_niceguy on 2008-12-25
have you tried intrepid? it has better support for hardware compared to other versions.

---

### Post by johnnyxf on 2008-12-25
Hi.
Yes, I have just looked  that up. It uses 2.6.27, which does not have the fix. Nae luck.

---

### Post by rvergara on 2009-02-22
Hi all,

Read this (and others) thread before buying a good deal for a new ASUS box with the ASUS P5SD2-VM motherboard with built-in SiS network adapter 191.

When I went for the box I asked a good old RTL 8139 PCI card to be installed. Cost for this additional was $6 . I installed Ubuntu 8.10, as anticipated the integrated network did not work but just to switch to the RTL 8139 and I was browsing in no time. I guess $6 was not worth the time I would have to spend to fix the issue. Hopefully 9.04 will solve the issue but in the meantime I am happy.

Regards

Ramiro

---

