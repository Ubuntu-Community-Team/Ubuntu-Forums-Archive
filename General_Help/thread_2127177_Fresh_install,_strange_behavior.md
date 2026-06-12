---
title: "Fresh install, strange behavior"
date: 2013-03-19
forum: General Help
---

### Post by Chew N Tobacca on 2013-03-19
I recently put together an entire new machine (components listed in signature), and after running it for a while in different Live OSes, I knew it was stable and time to install. Naturally, I installed Win7 first, and all went smooth. Runs great. Without hesitation, I installed Kubuntu 12.04 LTS, which I run on my laptop and had run on my old desktop. The installation went well, and it boots up great in no time flat. 

However, it is behaving rather strangely, and I have no idea where to start troubleshooting. Everything seems to be recognized and work fine, just not in a timely manner. Here are a few examples: 

- I can open the System Settings dialog and it opens right up. But then upon trying to open a sub-dialog, it pauses for a minute, maybe two. In the meantime, the mouse moves and the widgets (CPU / Temp) will continue to move; the rest of the system is (usually) unresponsive. Nothing can be opened or clicked until the system catches up. 
- Similar behavior has been experienced when trying to open Dolphin. Once open it functions properly until trying to exit. It must be terminated to exit.
- The same thing happens when even trying to shut down or restart. I can pull down the applications menu and click "shut down" but the system waits, again, a minute or two before responding. 

Also, the mouse cursor occasionally flashes or disappears completely until it is moved. Desktop effects also seem to not be functioning completely. (i.e. changing virtual desktop does not scroll or cube rotate.)

Thanks in advance for any advice or suggestions.
-Chew

---

### Post by stinkeye on 2013-03-19
Post your GFX info
```
lspci -k | grep -A3 VGA
```

---

### Post by Chew N Tobacca on 2013-03-19
Per request, here is the output of the lspci command:

$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 683d
        Subsystem: ASUSTeK Computer Inc. Device 045d
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx_updates

FYI - The 3rd party driver is installed.

-Chew

---

### Post by Chew N Tobacca on 2013-03-21
*Update*

Been trying to figure this out, but to no avail. I have removed and re-installed the VGA drivers, and seems to be installed and functioning normally. Catalyst runs properly (near as I can tell); the hardware is recognized and listed just fine.

The issues I am having are similar to the conditions [described by the OP here]("http://http://www.kubuntuforums.net/showthread.php?58512-Kubuntu-12-04-very-slow-in-performance"). In my case, it is not any/every application that is slow to open; here's to name a few: Dolphin file manager, power management, restart/logout/shutdown. Probably more, but these are what I've found. It actually takes several minutes for these to start after opening/clicking. Most everything else is speedy as to be expected, including startup. 

Also in searching, I have discovered that none of the Startup Services are running at all. In order to even access the Service Manager, I have to be root. I can start anything individually and causes MOST of the rest to start, but nothing starts on login. After logout/restart, none of the services start.

Any suggestions?

Thanks,
-Chew

EDIT: I think it may be useful to re-emphasize the fact that Windows 7 is also on this machine, and it runs wonderfully. So I know my hardware is fine.

---

