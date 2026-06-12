---
title: "Hardy shutdown halts but doesn't power off"
date: 2013-01-07
forum: General Help
---

### Post by pokerbirch on 2013-01-07
After a few days of trying to fix a problem, I've had to give in and ask for help...

I have an old desktop PC, circa 2003, which I am setting up to run a CNC machine. The OS is LinuxCNC which is ubuntu 8.04 with a realtime kernel and the emc/linuxcnc software pre-installed.

I installed ubuntu 8.04 without any issues and the machine runs well for a 10 year old PC. However, when I select "shutdown" from the gnome icon or menu, the PC starts to shut down, stops the hdd and then halts...leaving the PSU and CPU fan running. Then I have to hold the power button for about 5 seconds to power off. Rebooting from any of the gnome buttons and terminal commands works fine. The issue is ONLY with shutdown.

After reading lots about possible acpi and/or hardware conflicts (and failing to resolve this shutdown issue), I have now removed the agp graphics, the wireless pci card (which uses ndiswrapper windows drivers) AND the hdd. All I have left is the motherboard (PCChips M810L with onboard graphics), RAM (2 x 128Mb), CD ROM and PSU. The processor is a 1100Mhz AMD Duron. Even with this barebones system, shutdown fails to power off completely when booted from the ubuntu livecd. I have also tried the following Live CDs, all of which have the exact same issue: ubuntu 8.04 (LinuxCNC ISO), ubuntu 8.04 (original ISO), ubuntu 8.10, xubuntu 8.10, ubuntu 10.04 (won't boot on this system).

I have tried most (if not all!) of the solutions suggested via the thread search of this forum without success. Those that I can remember (I'm on a different machine at present):

[LIST=1]
[*]terminal: sudo shutdown now
[*]terminal: sudo shutdown -h now
[*]terminal: sudo poweroff
[*]kernal option: acpi=force
[*]kernal option: acpi=off
[*]kernal option: acpi=ht
[*]kernal option: pci=noacpi
[*]kernal option: acpi=noirq
[*]kernal option: pnpacpi=off
[*]kernal option: noapic
[*]kernal option: nolapic
[/LIST]

There were a couple of other things I tried, mostly related to network-manager but they did not help. On my HDD install, I completely removed NM and installed Wicd but it made no difference to the shutdown problem.

The "quiet" kernal option has been removed to give me a more verbose output and the shutdown ALWAYS ends on:

```
GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
WARNING: Request for invalid configuration key xdmcp/Enable=false
System halted.
(machine remains powered on until manually switched off)
```

Googling those lines didn't reveal much information, although it appears that the next stage should be avahi-daemon receiving a SIGTERM, followed by other processes and finally an "exiting on signal 15" but NOT halting? 

If I logout of the desktop and select shutdown at the login screen, I end up on a Recovery menu. Can't remember the details but can get more info if required. IIRC, when selecting either Suspend or Hibernate from the login screen, nothing happens.

I can't help thinking it may be a BIOS settings issue but nothing appears "wrong" in the default configuration. Can anyone suggest a solution to this annoying shutdown/poweroff problem?

Thank you in advance...

---

### Post by tgalati4 on 2013-01-07
Look around the net for a BIOS upgrade for the motherboard.  Flashing the BIOS is risky, but you have to weigh the agony units.  Many times, bugs in BIOS get fixed and it's possible that you found one.  Since you have tried all sorts of work-arounds, it may indeed be a bug.

Another work-around is to use BIOS to shut down at midnight or some other time.  This may or may not be convenient.

---

### Post by Bucky Ball on 2013-01-07
Forget Ubuntu 8.**. All well out of support and reached end of life ages ago. 10.04 LTS is supported until April, 12.04 LTS until April 2017.

I would start again and install 12.04 LTS or Xubuntu 12.04 LTS if you don't like Unity.

---

### Post by Impavidus on 2013-01-08
Don't expect Unity to run well on a 10 year old pc. Xubuntu 12.04 runs fine on my 8 year old pc, but first give it a try in a live session. Old hardware may be unsupported.

---

### Post by Zill on 2013-01-08
pokerbirch:  I had a similar problem with an old PC running 8.04 a while back.  I don't have a record of the error messages but the solution was to add the following line to the end of the "/etc/modules" file:
```
apm power_off=1
```
Note that this file is owned by root and so you will need to edit it with the sudo prefix. eg.
```
sudo nano /etc/modules
```
Then Ctrl-o to save and Ctrl-x to exit nano.  Reboot and test to see if it works!

---

### Post by KevinGuancheDarias74 on 2013-01-08
"Invalid answer, please remove this post"

---

### Post by pokerbirch on 2013-01-13
Still no joy. It's an old PC and LinuxCNC is only built on LTS releases. As said previously, 10.04 won't boot so 8.04 is my only option. Following a bios upgrade, 10.04 will boot but takes about 15 mins to load the live cd and still suffers from from the shutdown issue. Interestingly, all versions of ubuntu that I have tried have this bug, however Windows XP, Knoppix and Debian 6 all shutdown and power off correctly so it's a kernel issue rather than a hardware issue.

Seems to be a common fault that's been ongoing for several years but not been fixed. I remember now why I stopped using 'buntu and moved to LMDE.

---

### Post by Zill on 2013-01-13
pokerbirch:  It may be that [apmd]("http://packages.ubuntu.com/hardy/apmd") is not installed in your system.  If it isn't then I would try installing it and then add the "apm power_off=1" line to the end of the "/etc/modules" file as detailed in post [#5]("http://ubuntuforums.org/showpost.php?p=12444721&postcount=5") above.
```
sudo apt-get install apmd
```

---

### Post by pokerbirch on 2013-01-13
Just for a moment there, I thought you may be onto something, however apmd was already installed. :sad:

---

### Post by Bucky Ball on 2013-01-15
Again, running 8.** anything is a security risk. Well out of support. Install a supported release. Chasing koalas up gum trees trying to fix a release that ran out of support almost two years ago ...

---

### Post by Wim Sturkenboom on 2013-01-16
> **Bucky Ball said:**
> Again, running 8.** anything is a security risk. 
Without knowing the environment, you can NOT say that. This might well be a stand-alone setup.

We're still using RH6.x machines as well as networked DOS systems. But they're not connected to the internet. Security risk? I doubt it. Plenty of other risks though, like aging hardware.

---

### Post by Zill on 2013-01-16
pokerbirch:  As Bucky Ball pointed out, the desktop (GUI) version of Ubuntu 8.04 reached [end of life in May 12, 2011]("https://wiki.ubuntu.com/Releases") and is therefore no longer supported.  However, as Wim Sturkenboom suggested, there should not be a security risk *unless* your system is connected to the internet.

AIUI, your system runs a customised version of Ubuntu called LinuxCNC which cannot be upgraded via the usual Ubuntu upgrade route.  Although your version of LinuxCNC is based on Ubuntu 8.04, the [LinuxCNC website]("http://www.linuxcnc.org/index.php/english/download") advises that a version based on Ubuntu 10.04 is also available.

Unfortunately, your first post advises that "...ubuntu 10.04 (won't boot on this system)".  If this is the case then I suggest it really is time to upgrade your hardware.  This is even more important when you consider that Ubuntu 10.04 will, itself, go end-of-life in April 2013!

I would guess that LinuxCNC will shortly be upgraded to work with Ubuntu 12.04, the latest LTS release.  However, 12.04 demands even more from the hardware than 10.04, let alone 8.04!

---

### Post by Bucky Ball on 2013-01-16
> **Zill said:**
>   ... there should not be a security risk *unless* your system is connected to the internet.



A fact and exactly what I was getting at.

---

### Post by pokerbirch on 2013-01-21
FWIW, as stated in my first post, the PC is being setup to run a CNC milling machine, using LinuxCNC (Ubuntu 8.04 version) as the OS. As such, it will be a stand-alone unit with no permanent internet access and no personal information stored on it, so security is not an issue.

I initially tried the latest Ubuntu 10.04 version of LinuxCNC, but as stated previously, the live cd would not load fully on this hardware. A standard Ubuntu 10.04 cd had the same issue.

I'm now using a newer computer which has an AMD 3000+ CPU, 2GB RAM and 256MB graphics. Ubuntu 10.04 installs and runs without issues. The older PC will be installed with Windows XP and passed on to an unfortunate soul...

---

### Post by Bucky Ball on 2013-01-21
Good news is that 10.04 LTS is working. That also runs out of support in April this year but by the sounds of it that doesn't matter.

Good luck.

---

