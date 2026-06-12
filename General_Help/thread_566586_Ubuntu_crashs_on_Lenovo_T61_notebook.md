---
title: "Ubuntu crashs on Lenovo T61 notebook"
date: 2007-10-03
forum: General Help
---

### Post by jingdejun on 2007-10-03
According to [this post]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61") I installed Ubuntu 7.10 on my T61 laptop.

At beginning everything worked fine for a period of time after installation, but the system began to crash, especially after I did not touch the laptop for a while. A typical symptom is the system freezes, and the light of 'Capt Lock' continues to blink....

Anyone know why this happen? Thanks.

---

### Post by devmage on 2007-11-24
I'm getting the same thing on my T61.  Seems to be mostly unpredictable.  I use my laptop for roughly 6 hours per day, and it occurs usually once in that span.  I browsed through my system logs with gnome-system-log, and found nothing out of the ordinary at the time of the lock-up.

I am running Gutsy x86-64 on the 2.6.22-14 kernel.  My video is through the proprietary Nvidia driver, using an Nvidia Quadro NVS 140M.  My wireless is through madwifi, using an Intel 3945ABG chip.  I can post more system information if needed.

I am actively searching for a solution, but anyone with a definitive answer is more than welcomed!

Edit: The crash occurs more often for me when I am actively using the laptop, not when it is idle.  The entire system locks up and will not software-reboot, log out, or switch to virtual terminals - it is like a full kernel panic.  The caps-lock light blinks as described.

---

### Post by devmage on 2008-01-08
So I've had some time to play with it, off and on.  I've narrowed the issue down to one involving the wireless chip.  The chip reports as:

```
lspci | grep "Ath"
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

I have no problem at all using the system for days on end via wired ethernet.  From my knowledge, the Atheros chip above is part of a mini-PCIE card.  I'm on the wireless right now, and from what I've been able to tell there is no way to predict a crash.  Periods of higher data transfer (i.e. if I were to go on Youtube) seem to trigger it more often, but even just idling on IRC is enough.

Any suggestions?

I'll keep monitoring syslog, messages, etc. for anything out of the ordinary around crashes.

---

### Post by devmage on 2008-01-08
So I managed to catch a crash!  The following are snippets of various log files at the moment of the crash.  If anyone can make sense of things, please let me know - it all looks normal to me.

20:59:54 was roughly when I brought the system back up from the crash.

From /var/log/messages:
```
Jan  8 19:45:19 delta -- MARK --
Jan  8 20:05:19 delta -- MARK --
Jan  8 20:25:19 delta -- MARK --
Jan  8 20:45:19 delta -- MARK --
Jan  8 20:59:53 delta syslogd 1.4.1#21ubuntu3: restart.
Jan  8 20:59:54 delta kernel: Inspecting /boot/System.map-2.6.22-14-generic
Jan  8 20:59:54 delta kernel: Loaded 26085 symbols from /boot/System.map-2.6.22-14-generic.
Jan  8 20:59:54 delta kernel: Symbols match kernel version 2.6.22.
Jan  8 20:59:54 delta kernel: No module symbols loaded - kernel modules not enabled. 
Jan  8 20:59:54 delta kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
```

From /var/log/syslog:
```
Jan  8 20:45:19 delta -- MARK --
Jan  8 20:59:53 delta syslogd 1.4.1#21ubuntu3: restart.
Jan  8 20:59:54 delta kernel: Inspecting /boot/System.map-2.6.22-14-generic
Jan  8 20:59:54 delta kernel: Loaded 26085 symbols from /boot/System.map-2.6.22-14-generic.
Jan  8 20:59:54 delta kernel: Symbols match kernel version 2.6.22.
Jan  8 20:59:54 delta kernel: No module symbols loaded - kernel modules not enabled. 
Jan  8 20:59:54 delta kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
```

From /var/log/debug:
```
Jan  8 15:46:06 delta kernel: [   75.545931] ath0: no IPv6 routers present
Jan  8 15:46:20 delta kernel: [   85.064305] ath0: no IPv6 routers present
Jan  8 16:53:02 delta kernel: [ 1652.274390] Monitor-Mwait will be used to enter C-3 state
Jan  8 20:59:54 delta kernel: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Jan  8 20:59:54 delta kernel: [    0.000000] Entering add_active_range(0, 256, 515760) 1 entries of 3200 used
Jan  8 20:59:54 delta kernel: [    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
Jan  8 20:59:54 delta kernel: [    0.000000] Entering add_active_range(0, 256, 515760) 1 entries of 3200 used
Jan  8 20:59:54 delta kernel: [    0.000000] On node 0 totalpages: 515661
Jan  8 20:59:54 delta kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jan  8 20:59:54 delta kernel: [    0.000000]   DMA zone: 1125 pages reserved
Jan  8 20:59:54 delta kernel: [    0.000000]   DMA zone: 2816 pages, LIFO batch:0
Jan  8 20:59:54 delta kernel: [    0.000000]   DMA32 zone: 6995 pages used for memmap
Jan  8 20:59:54 delta kernel: [    0.000000]   DMA32 zone: 504669 pages, LIFO batch:31
Jan  8 20:59:54 delta kernel: [    0.000000]   Normal zone: 0 pages used for memmap
```

From /var/log/acpid (just in case it was a weird power issue somewhere):
```
[Tue Jan  8 20:57:17 2008] BEGIN HANDLER MESSAGES
[Tue Jan  8 20:57:17 2008] END HANDLER MESSAGES
[Tue Jan  8 20:57:17 2008] action exited with status 0
[Tue Jan  8 20:57:17 2008] completed event "battery BAT0 00000080 00000001"
[Tue Jan  8 20:59:53 2008] starting up
[Tue Jan  8 20:59:53 2008] 72 rules loaded
[Tue Jan  8 20:59:54 2008] client connected from 5313[107:116]
[Tue Jan  8 20:59:54 2008] 1 client rule loaded
[Tue Jan  8 21:00:03 2008] client connected from 6257[0:0]
[Tue Jan  8 21:00:03 2008] 1 client rule loaded
[Tue Jan  8 21:00:05 2008] client connected from 6257[0:0]
[Tue Jan  8 21:00:05 2008] 1 client rule loaded
```

I don't see anything out of the ordinary.  Whatever the problem, it isn't being logged.

---

### Post by aleiderman on 2008-02-09
Just dropping by to check if someone found what the issue is with the lockdowns and system freezes. Tried installing the latest kernel (2.6.24.7 Generic) but still get the freezes when trying to use my computer in a wireless connection.

Reading other threads, I believe that this issue only happens using the 64 bit version of Ubuntu 7.10.

On another thread I read that maybe using ndiswrapper to use the windows driver for the wireless card instead of the native linux driver may resolve the issue, but really haven't tried that solution yet. If anyone was able to solve this problem, please let me know.

Thanks in advance,

Abraham

---

### Post by lunatico on 2008-02-10
Hello!

I have 7.10 running on a T61 which has the Atheros 5212 wifi card (using madwifi drivers) and I experience no crashes at all. I did had problems before with the right side usb ports... I updated my BIOS firmware to the latest and everything was fixed. I would recommend that. By the way, do you experience low wireless reception? I'm 1.5 meters from the router and I get 60% signal.

Cheers!

---

### Post by aleiderman on 2008-02-11
Hi,
My T61 runs on the intel 4965 wireless interface, and getting 85% signal while standing at 2 meters from the router.

AL

---

### Post by matey3 on 2008-02-11
Lot of good things said about t61:

[http://www.businesswire.com/portal/site/google/index.jsp?ndmViewId=news_view&newsId=20070509005551&newsLang=en](http://www.businesswire.com/portal/site/google/index.jsp?ndmViewId=news_view&newsId=20070509005551&newsLang=en)

but I know some one who had crashing problems, it turned out to be the cooling fan(s) could not move any air thru ,bcs the opening 4 the air was clogged by lint and other debris. theirs was a compaq where the air hole is at the bottom of the laptop (where it should never be , if we call it a "lap-top" any way bcs your pants/bed sheets etc do have a lot of extra lint to spare) ;-)
I brushed and vaccuumed the stuff off,  the laptop works like new now!
you know i was trying to tell them on the phone but they could not recognize the problem bcs it (the dirt) looked like a perfect grey circle (looked built- in) heh and they thought it should have been there?!
anyway..
just a thought...

---

