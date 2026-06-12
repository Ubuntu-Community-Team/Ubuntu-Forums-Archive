---
title: "Problem with the power saving mode - Raspberry Pi 4"
date: 2020-11-12
forum: General Help
---

### Post by autominus on 2020-11-12
Hi,
I have a problem with new version of Ubuntu Desktop 20.10 on Raspberry Pi 4. 
When I turned on the microcomputer and I didn't logged in long time in my account, the monitor entered power save mode.
When I use any key on keyboard or any button on the mouse, I see the GDM login screen. However, at this point the keyboard and mouse stop working and I can't login to system. In addition, The mouse LED lights continuous lights. It looks like the system has crashed.

Unplugging the power adapter from the power outlet only helps.

Thank you in advance for your help.

---

### Post by HermanAB on 2020-11-13
Look at the system log files.  That is pretty much all you can do - apart from googling the problem to see whether others also encountered it.

---

### Post by autominus on 2020-11-14
I looked through the logs but I found nothing.
When my operating system crashes, it on the RPi4 only red LED lights continuous lights.

**journalctl**
lis 14 20:09:23 I'm logging out of the Gnome
lis 14 20:15:00 GDM goes to power save mode. Monitor turns off.
lis 14 20:18:22 I use any key on the keyboard or any button on the mouse. Monitor turns on and the system crashed - I see the GDM login page, but keyboard and mouse not working.[INDENT][https://filebin.net/gf1il0rby5thlhkg/journalctl.txt?t=1b0j1e3j](https://filebin.net/gf1il0rby5thlhkg/journalctl.txt?t=1b0j1e3j)
[/INDENT]

**dmesg**[INDENT][https://filebin.net/pbhgq1u7naxcki9h/dmesg.txt?t=99tgtftq](https://filebin.net/pbhgq1u7naxcki9h/dmesg.txt?t=99tgtftq)
[/INDENT]

**lspci -k**
```

00:00.0 PCI bridge: Broadcom Inc. and subsidiaries Device 2711 (rev 10)
    Kernel driver in use: pcieport
01:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
    Subsystem: VIA Technologies, Inc. VL805 USB 3.0 Host Controller
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci

```

I shared the log files on an external server. 
dmesg.txt - 37,4 kB --> [https://filebin.net/pbhgq1u7naxcki9h/dmesg.txt?t=99tgtftq](https://filebin.net/pbhgq1u7naxcki9h/dmesg.txt?t=99tgtftq)
journalctl.txt - 212,1 kB --> [https://filebin.net/gf1il0rby5thlhkg/journalc tl.txt?t=1b0j1e3j]("https://filebin.net/gf1il0rby5thlhkg/journalctl.txt?t=1b0j1e3j")

---

