---
title: "Time to get to the bottom of this"
date: 2007-04-14
forum: General Help
---

### Post by Cirdan7 on 2007-04-14
Ok, my desktop PC has had random freezes(Fiesty). I have posted in the past about this problem and it has yet to be resolved. Its not bad hardware because my Windows partition runs as flawlessly has Windows can run. There are no errors in the logs, and I have installed the dual core kernel(smp) but no change. What should I try and how do I do it? Someone has recommended that I try disabling all of the modules and re enabling them one by one. How do I go by doing this? I'd love to be able to run Linux without a hitch, but with this random freezing its impossible. I am using wireless, but its an Ethernet converter, so no drivers are needed.

---

### Post by PointSource on 2007-04-14
You could try going for an earlier version of ubuntu, that might fix it if your problem is related to unstable/new features/drivers.

Having hardware working fine in windows doesn't mean much at all, driver wise.

---

### Post by tictacman on 2007-04-14
You should find a list of modules in /etc/modules.  To remove a module I think its just 

```
sudo modprobe -remove nameofmodule
```

How often do the random freezes occur? Have you tried running ubuntu without this nik converter at all? 

It would probably be a good idea if you post your hardware specs as it might everyone something to work on:

---

### Post by Cirdan7 on 2007-04-14
System Specs:
Pentium 4 Dual-Core Hyper Threaded 3ghz
1 gig of ram
ATI Radeon 9700

What I have tried and failed:
Turned off Hyper-Threading in the bios.
Turned off Beryl.
Unplugged bad DVD Drive
Cannot ping the system when frozen.
CTRL-ALT-BACKSPACE doesn't do anything
CTRL-ALT-F1 doesn't do anything.
Windows runs fine on the same machine,slow, but it doesn't freeze.
Running it from the CD also freezes randomly.

I am using Buffalo Airstream Turbo G for my wireless.

---

### Post by jfinkels on 2007-04-14
Perhaps try Ubuntu 6.10, (Feisty *is* still beta, at least for a few more days :P)

---

### Post by Cirdan7 on 2007-04-14
It was doing the same thing with Edgy....unfortunatly. Stopping gnome-power-manager helps.

---

### Post by tictacman on 2007-04-14
I wonder if it is something to do with acpi?  That has been known cause system freezes according google . Acpi can be turned off in grub if needed.

---

### Post by bulldog on 2007-04-14
Windows shouldn't run 'slow' on a 3GHZ pentium machine.
Did you check if the dma option is enabled in your BIOS and ubuntu as well?

Did you run a RAM check to see if the RAM is faulty?

---

### Post by Cirdan7 on 2007-04-14
> **bulldog said:**
> Windows shouldn't run 'slow' on a 3GHZ pentium machine.

Thats what I thought, but I guess I'm wrong. Maby my hard drive is going bad.

> **bulldog said:**
> Did you check if the dma option is enabled in your BIOS and ubuntu as well?

Did you run a RAM check to see if the RAM is faulty?

I did do a memcheck86, but it didn't find anything, and if the memory was bad....windows would be crashing more then it does. I have not checked the DMA option, I don't even know what it is.


I have tried turning off APCI(via grub) and that didn't do anything.

---

### Post by tictacman on 2007-04-14
> Maby my hard drive is going bad.


You said earlier that running from cd, which I take to mean a live distro, also freezes your system.   Would have thought that would have ruled out your hard drive.  

What does > Unplugged bad DVD Drive mean? Have you got faulty dvd drive?  Perhaps thats why livecds fail.

Have you checked ide/sata cables to make sure they are securely connected (though I would have thought such a problem would have caused windows to freeze up as well). Have you tried replacing the cables?

edit: srry if that sounds a bit gruff, just presenting ideas :)

---

### Post by Cirdan7 on 2007-04-14
I have two dvd drives, one of them is bad and sometimes won't read disks, I have tried unplugging it to see if its confusing the kernel, but it didn't help. I have checked the cables, but haven't tried replacing them.

---

### Post by Cirdan7 on 2007-04-14
Well...I reset my sources.list to default and did all of the updates so its completely up to do and so far it has not crashed, when it normally have already.


EDIT: Spoke too soon. It seems like running Compiz is actually helping it.

---

### Post by tictacman on 2007-04-15
If your still having problems you might also want to consider your power supply, poor supplies can play real havoc with a system.


good luck, hopefully you've got it sorted.

---

### Post by crag277 on 2007-04-24
I just wanted to know if anyone has found a solution to this problem.  I have a very similar system, and I am very confident that the problem lies with the Radeon 9700 video card and 3D rendering.

I was able to run Edgy with Gnome and no 3D desktop without a problem on my system, but whenever I tried Edgy/Feisty with KDE, or with 3D rendering (both radeon and fglrx drivers) I experienced hard freezes after several minutes of use.  This same problem occurs running MEPIS 6.5 too.

I can live without the 3D desktop, but it would be nice to get this resolved, because when it is working it works very well.  I'd try another video card, but I don't have another one.

Here's my system:
Asus P5PE-VM (Intel 865) (brand new)
P4 Prescott 3.2 GHz (brand new)
1GB Corsair RAM (older, but never any problems in any other OS')
ATI Radeon 9700 Pro AGP (oldest part in the PC)
2x Seagate SATA drives
Zalman 460wt PS (brand new)

Thanks for any help

---

### Post by tgalati4 on 2007-04-24
Overheating video chips is definitely a candidate.  Try declocking your CPU's to 1/2 speed and see if reliability improves.  Add lm-sensors and try to monitor your temperatures.  Add smartmontools and monitor your disks.  Pull out a power supply feed (through the case) and hook it up the 12V lead to a digital multimeter and watch it during use.  Do the same for 5V.  Look for fluctuations during operation.  lm-sensors can also pull out voltages internally, including CPU core voltage which is critical.  

The ATI radeon 9700 is a workhorse but it may not be able to sync correctly with the 3 GHz core system.  Does the Asus board have on-board video?  If so, remove the ATI and run with onboard video for a while.

Ubuntu systems can be reliable.  I had a Dapper system with 165 days of uptime and about 100 deferred system updates.  You wouldn't drive a car on the freeway if it randomly cut out without warning.

---

