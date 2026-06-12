---
title: "My monitor hates me"
date: 2008-06-05
forum: General Help
---

### Post by avianbc on 2008-06-05
I'm using 8.04 and I'm having problems with my monitor. Every time I turn it off using the power button on the monitor, it never comes back on when I click the power button again... it says it gets no signal. Same thing happens when I leave my PC on overnight seeding torrents. I have screensavers and power management off but when I wake up I always have a blank screen and have to Control-Alt-Backspace and restart X every day and its quite annoying. How would I go about troubleshooting this?

Heres my specs (I'll post more if you need them):
Ubuntu 8.04
ATI Radeon 9550 w/ ATI restricted driver
Westinghouse 19" widescreen monitor

If you need me to post my xorg.conf or anything else let me know.

Thanks in advance!

---

### Post by Sam Lars on 2008-06-05
Do you have your power settings disabled in BIOS as well?

---

### Post by avianbc on 2008-06-06
Yes, it is diabled there as well.

---

### Post by avianbc on 2008-06-06
Bump.

Would removing my current drivers and installing the propreitary drivers from [ATI's website]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") be a good idea?

---

### Post by Sam Lars on 2008-06-06
I guess it's worth a try.  ATI drivers don't tend to play well with Linux, though.  Just a mild warning.
Does any keyboard or mouse activity wake up the monitor, or is Ctrl+Alt+Backspace the only way out?

---

### Post by avianbc on 2008-06-06
Yep, all that responds is Control-Alt-Backspace. It wont let me change terminals or anything, so it seems like its X completely freezing.

---

### Post by Sam Lars on 2008-06-06
Have you disabled both the screensaver and the power preferences for the monitor?

---

### Post by avianbc on 2008-06-06
Yeah, I set put computer and display to sleep when idle to never. Also on the screensaver, I unchecked "Activate screensaver when computer is idle" and moved the slider out to 2 hours just incase.

I was doing some digging and I think I found something in /var/log/syslog (check the bold text):

> Jun  6 20:11:45 bobspc -- MARK --
Jun  6 20:17:01 bobspc /USR/SBIN/CRON[11168]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
**Jun  6 20:19:39 bobspc gdm[9558]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 **
Jun  6 20:19:39 bobspc Synergy 1.3.1: FATAL: CXWindowsScreen.cpp,1590: X display has unexpectedly disconnected
Jun  6 20:19:40 bobspc kernel: [72387.025660] [fglrx] interrupt source 10000000 successfully disabled!
Jun  6 20:19:40 bobspc kernel: [72387.025669] [fglrx] enable ID = 0x00000000
Jun  6 20:19:40 bobspc kernel: [72387.025673] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000005
Jun  6 20:19:40 bobspc kernel: [72387.025696] [fglrx] interrupt source 20008000 successfully disabled!
Jun  6 20:19:40 bobspc kernel: [72387.025700] [fglrx] enable ID = 0x00000000
Jun  6 20:19:40 bobspc kernel: [72387.025704] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000004
Jun  6 20:19:45 bobspc kernel: [72392.704120] [fglrx] Internal AGP support requested, but kernel AGP support active.
Jun  6 20:19:45 bobspc kernel: [72392.704129] [fglrx] Have to use kernel AGP support to avoid conflicts.
Jun  6 20:19:45 bobspc kernel: [72392.704135] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
Jun  6 20:19:45 bobspc kernel: [72392.704295] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jun  6 20:19:45 bobspc kernel: [72392.704318] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jun  6 20:19:45 bobspc kernel: [72392.704359] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jun  6 20:19:45 bobspc kernel: [72392.704385] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
Jun  6 20:19:45 bobspc kernel: [72392.712708] [fglrx] GART Table is not in FRAME_BUFFER range 
Jun  6 20:19:45 bobspc kernel: [72392.712726] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Jun  6 20:19:45 bobspc kernel: [72392.712730] [fglrx] Reserve Block - 1 offset =  0Xffff000 length = 0X1000
Jun  6 20:19:45 bobspc kernel: [72392.842742] [fglrx] interrupt source 20008000 successfully enabled
Jun  6 20:19:45 bobspc kernel: [72392.842753] [fglrx] enable ID = 0x00000004
Jun  6 20:19:45 bobspc kernel: [72392.842772] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Jun  6 20:19:45 bobspc kernel: [72392.842880] [fglrx] interrupt source 10000000 successfully enabled
Jun  6 20:19:45 bobspc kernel: [72392.842885] [fglrx] enable ID = 0x00000005
Jun  6 20:19:45 bobspc kernel: [72392.842892] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Jun  6 20:19:56 bobspc pulseaudio[15774]: pid.c: Stale PID file, overwriting.
Jun  6 20:20:01 bobspc Synergy 1.3.1: NOTE: synergys.cpp,500: started server
Jun  6 20:20:01 bobspc NetworkManager: <info>  Updating allowed wireless network lists. 
Jun  6 20:20:01 bobspc NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

I've noticed glxgears runs fine, but when I type fglrxinfo in a console and hit enter, my video gets all wacky and I have to control-alt-backspace so it restarts X and I can see what I'm doing.

---

### Post by Sam Lars on 2008-06-06
Have you tried using the ATI proprietary drivers yet?

---

### Post by avianbc on 2008-06-06
I think I may have fixed it. My monitor actually turns back on when I hit the power button now. Heres the link I used to fix it if someone else has the same problem as me:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

I'll leave my PC on seeding all night tonight and hopefully it wont freeze. If so, I'll be back to bump this thread.

Thanks for all the help, Sam.

---

