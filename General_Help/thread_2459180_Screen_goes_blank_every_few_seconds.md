---
title: "Screen goes blank every few seconds"
date: 2021-03-12
forum: General Help
---

### Post by akniss on 2021-03-12
It has been many years since I've posted here on the forums (hi again!), but I'm having a problem I've not been able to figure out from searching here or elsewhere. I have a Dell system in my office (purchased with Ubuntu pre-installed) that has started acting up in the months that I've been working from home. Basically, every 10 to 15 seconds, the screen (built-in screen as well as external monitor) will go blank for 1 to 2 seconds then come back on. Just before the screen blanks, I seem to lose mouse and keyboard (connected by bluetooth) functionality also, but I'm unsure whether that's real because it happens so quickly before the screen goes blank. 

System:
Dell Precision 5720 AIO (075D)
Intel(R) Core(TM) i7-7700 CPU @ 3.60GHz
Intel HD Graphics 630

Running Bionic (everything's up to date)
lsb_release -a:
Ubuntu 18.04.5 LTS
uname -a:
4.15.0-136-generic #140-Ubuntu SMP Thu Jan 28 05:20:47 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

I'm kind of guessing this is related to a driver, but am unsure where to start troubleshooting. I can ssh to the system from home and everything works fine, but can't work locally on the system at this point because the constant screen blanking issue makes it exceptionally frustrating and unproductive. I need to get it back up and running in preparation for returning to the office in the coming months. Any help figuring out this problem is appreciated.

---

### Post by DuckHook on 2021-03-12
Welcome back!

It sounds possibly like HW to me.

[LIST]
[*]Is your GPU subsystem or MOBO healthy?
[*]Is PSU outputting dependable power?
[*]Did it start happening immediately after an OS upgrade?
[/LIST]
I've had the sort of experience you describe with a video card that was on its last legs. It failed outright a few weeks later. But it could be other subsystems as well. OS is always a possibility: what do your logs say?

---

### Post by akniss on 2021-03-12
I've spent so many years running mostly trouble-free Ubuntu installations, I'm not even sure which logs to check... I suppose Xorg is my first guess, and there is a particular error that is repeated many, many times (FBDEV FBIOPUTCMAP) followed by a seg fault. I don't know whether this is related or even problematic, though.
From /var/log/Xorg.0.log:

```

... output above here removed ...
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[ 265.064] (==) FBDEV(0): DPMS enabled
[ 265.064] (--) RandR disabled
[ 265.064] (EE)
[ 265.064] (EE) Backtrace:
[ 265.065] (EE) 0: /usr/lib/xorg/Xorg (xorg_backtrace+0x4e) [0x55ca6cc0fe0e]
[ 265.065] (EE) 1: /usr/lib/xorg/Xorg (0x55ca6ca5e000+0x1b5b79) [0x55ca6cc13b79]
[ 265.065] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fabd32ad000+0x11390) [0x7fabd32be390]
[ 265.065] (EE) 3: /usr/lib/xorg/Xorg (RRProviderAutoConfigGpuScreen+0x42) [0x55ca6cb7d232]
[ 265.065] (EE) 4: /usr/lib/xorg/Xorg (InitOutput+0x5bd) [0x55ca6caf6c7d]
[ 265.065] (EE) 5: /usr/lib/xorg/Xorg (0x55ca6ca5e000+0x582d6) [0x55ca6cab62d6]
[ 265.065] (EE) 6: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf0) [0x7fabd2f03830]
[ 265.065] (EE) 7: /usr/lib/xorg/Xorg (_start+0x29) [0x55ca6caa0449]
[ 265.065] (EE)
[ 265.065] (EE) Segmentation fault at address 0x130
[ 265.065] (EE)
Fatal server error:
[ 265.065] (EE) Caught signal 11 (Segmentation fault). Server aborting

```

---

### Post by akniss on 2021-03-12
I honestly don't know whether it happened after an upgrade. I've been keeping the system up to date this year by sshing into it from home. So there have been regular updates and use, but without physical access I didn't find out about this issue until a couple weeks ago when I tried to use the computer on-site again. So it might be update related, but I don't have a good way to know.

---

### Post by DuckHook on 2021-03-12
You should also go through your dmesg, syslog and systemd's journal. I would not recommend posting those here without filtering/parsing first for relevancy. Journalctl output in particular is massive.

Your Xorg log definitely shows a problem, but can't tell from it alone whether it's to do with the kernel, Xorg or HW. Not much comes up with a web search either. Possibly a continuation of this: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1510970](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1510970)
…but unlikely. That was an old bug.

A few further things to try:

[LIST=1]
[*]Boot into Wayland. If problem disappears, then it's an Xorg issue. (After backing up all critical data, you might try reinstalling Xorg)
[*]Boot from LiveUSB of Bionic. If the problem disappears, then HW is definitely not the problem. (You may then wish to consider a clean reinstall)
[*]Boot a LiveUSB of Focal. If problem disappears then consider upgrading to the newer LTS. If so, I would not recommend a network upgrade. You want a clean virgin install so as not to inherit the problem whether it is a misconfiguration or corrupted driver.
[/LIST]
Wish there was an easier way, but bug hunting is a tough and dirty exercise.

---

### Post by akniss on 2021-03-13
I bit the bullet last night and did a do-release-upgrade to 20.04. Rebooted when all updates were finished and everything seems to be working and stable again. So I'm not sure what the configuration problem was causing the issue, but the default 20.04 settings seem to have fixed the problem.

---

