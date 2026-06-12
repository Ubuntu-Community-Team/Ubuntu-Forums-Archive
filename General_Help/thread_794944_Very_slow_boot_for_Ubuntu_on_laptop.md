---
title: "Very slow boot for Ubuntu on laptop"
date: 2008-05-15
forum: General Help
---

### Post by SpinningAround on 2008-05-15
There is a problem when i boot my laptop, it works fine almost most of the time, but at one point (think around the Ethernet) does the boot stop for 1-3min for then continue as nothing has happened. I'm unsure why it stop at that point, any way to find out?

---

### Post by housam on 2008-05-15
I think it could be due to trying to connect to the internet while booting. Disconnect the internet connection and see if it is booting normally.

---

### Post by SpinningAround on 2008-05-15
> **housam said:**
> I think it could be due to trying to connect to the internet while booting. Disconnect the internet connection and see if it is booting normally.

That is the strange part, there is no network cable plugged in, only used it during the installation since my WLAN don't work from start.

---

### Post by housam on 2008-05-16
Look at [[COLOR="Red"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=580903") it may help

---

### Post by ugm6hr on 2008-05-22
Did the LiveCD boot OK?

Do you get a "Splash" (animated) boot screen?

It may well be a screen resolution issue - but only if you don't get a bootsplash screen.

What do you mean by "around the ethernet?"

---

### Post by SpinningAround on 2008-05-23
> **ugm6hr said:**
> Did the LiveCD boot OK?

Do you get a "Splash" (animated) boot screen?

It may well be a screen resolution issue - but only if you don't get a bootsplash screen.

What do you mean by "around the ethernet?"

Did simply run the installation, didn't bother testing the live cd, but I did go throw the normal installation. I don't think it's the resolution since i got that problem with 7.10 and the loading didn't stop as it do now, the loading bar that go back and forth simply stop now of then continue later, I got the bootsplash.

When I run it throw the recovery mode does it stop totally at or precise after the following message.

**[25.717073] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)**
and precisely after when it start loading again.
**clocksource tsc unstable**
unsure what since the text disappear quite quickly when it start loading other things.

---

### Post by SpinningAround on 2008-05-24
From the /var/log/syslog

May 15 10:02:32 linux-laptop kernel: [   27.601122] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May 15 10:02:32 linux-laptop kernel: [   27.677070] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
May 15 10:02:32 linux-laptop kernel: [   28.480700] Clocksource tsc unstable (delta = -1976285756 ns)
May 15 10:02:32 linux-laptop kernel: [   28.484717] Time: acpi_pm clocksource has been installed.
May 15 10:02:32 linux-laptop kernel: [   28.487171] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
May 15 10:02:32 linux-laptop kernel: [   28.487175] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pio

---

