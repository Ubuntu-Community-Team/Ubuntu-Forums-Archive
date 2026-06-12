---
title: "Power Outage = No GUI?"
date: 2015-04-30
forum: General Help
---

### Post by jim109 on 2015-04-30
I installed a system with Ubuntu 14.04 .02LTS x64 and configured it to control some hardware at our site.  Everything worked fine until we lost power one day.   When the power returned, the GUI wouldn't load.  This is a bad thing, as though the the hardware control daemon is running and operational, all of the settings are all done in X and I'm unable to change anything without a GUI.   The system boots and when it gets to the point that X starts, my monitor goes black and the ASUS auto-adjust pops up 3 separate times over ~10 seconds, but that's it.  The LCD thinks that it's getting a signal of 848x480 @ 70 htz, but nothing is ever displayed on the screen except black.  Nothing happens if I hit Control-Shift-Backspace, Control-Shift-+, or even Control-Alt-Delete.  Control-Alt-Delete DOES work if I press Control-Alt-F2 and then Control-Alt-Delete, rebooting the system cleanly.   Here's where it gets really weird.  If I hold down Shift when booting, choose recovery mode, mount the drive RW in any way, and then select Resume, I can get into X.  However, it's limited to 1024x768 and gives me errors when logging in, saying 'The system is running in low-graphics mode.  Your screen, graphics card, and input device settings could not be detected correctly.  You will need to configure these yourself.'  Running xrandr to add a 1440x900 mode yields no results.  While 1024 is far from ideal with my 29" LCD, it's at least functional.  Before the power failure, it was a normal ubuntu box.  I tried copying the relevant bits from the /etc/X11/xorg.conf file on a BSD unix machine to this one, but it had no effect.  I know the LCD is fine because this machine is on a 16-port KVM and all the rest function normally.   I don't feel like I should need (or want) to jump through these hoops every time the system reboots though and would appreciate some help in resolving the issue.  I was thinking that the graphics card took a poop due to the power failure, but why would it work when going through recovery mode?  (Same with any other hardware-failure type scenario... just does not make sense that it has to go into recovery mode before it's operational even in low-resolution mode.)

---

### Post by sandyd on 2015-04-30
Hi, can you do the following steps:
[LIST=1]
[*]Boot normally
[*]Shut it back down
[*]Go to recovery mode
[*]Attach /var/log/Xorg.0.log
[/LIST]

This will allow us to view any errors that are causing the GUI to not startup after boot.

---

### Post by Bashing-om on 2015-04-30
jim109; Hello;

My thoughts, a power failure -- an unproper shut down of the system and no telling what all files are left open and in an inconsistent state. The 1st thing I always do when power is restored is run a file system check (fsck).

Once that is done, then we can look at the graphics situation.
What the hardware is that we are working with:
```

lspci -vnn | grep VGA -A 12

```

What the software is doing:
```

sudo lshw -C display

```

See if there is an indication of what/where the problem is:
```

cat /var/log/Xorg.0.log

```

Maybe then, depending (RE-)install the graphics driver  ???

[INDENT][INDENT][INDENT]maybe
[INDENT][INDENT][INDENT]maybe not
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-04-30
Either from your low-res GUI or better from a Ctrl+Alt+F1 command-line if you can get to it, run command ```
sudo touch /forcefsck
``` then ```
sudo reboot
```

That will force the machine to run a filesystem check (fsck) at next boot, which might solve everything for you.

---

### Post by jim109 on 2015-05-04
Thanks for the responses.

  Sorry - should have mentioned that I did an fsck.  It's so automatic for me after an improper shutdown that I don't even think of it anymore.  Interesting tidbit about forcing it at boot by a flag file in the root directory of the file system though.

  I removed the X log, then rebooted into normal mode, then again into recovery mode & copied the X log to a flash drive and [put it on pastebin](http://pastebin.com/ZVNzZ9gZ).  I don't see much in it...

  The output from lspci -vnn is:
 ```
 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
 	Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
 
 00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
 	Flags: fast devsel
 	Capabilities: [80] HyperTransport: Host or Secondary Interface
 
 00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
 	Flags: fast devsel
 
 00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
 	Flags: fast devsel
 
 --
 01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS482/RS485 [Radeon Xpress 1100/1150] [1002:5974] (prog-if 00 [VGA controller])
 	Subsystem: Hewlett-Packard Company DC5750 Microtower [103c:280a]
 	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
 	Memory at c8000000 (32-bit, prefetchable) [size=128M]
 	I/O ports at 1100 [size=256]
 	Memory at d8500000 (32-bit, non-prefetchable) [size=64K]
 	[virtual] Expansion ROM at d8520000 [disabled] [size=128K]
 	Capabilities: [50] Power Management version 2
 
 01:05.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RS480 [Radeon Xpress 1150] (Secondary) [1002:5874]
 	Subsystem: Hewlett-Packard Company Device [103c:280b]
 	Flags: bus master, 66MHz, medium devsel, latency 32
 	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=128M]
 
```
 
 
 I also found the following in the /var/log/syslog file while poking around logs... does it mean anything?  FYI, the machine has a VGA connector (in use) and DVI (unused as the KVM is VGA-only).
  May  4 10:34:14 server4 kernel: [   15.693750] [drm:radeon_get_legacy_connector_info_from_bios] *ERROR* Unknown connector type: 8
 

  Here's something interesting that I discovered while trying to copy the log file off the machine... networking is disabled by default in recovery mode, so I selected the menu option to enable networking.  This paused a long time (~2 minutes), so I hit control-C, thinking that it'd interrupt whatever was froze & return me to the recovery menu.  Instead, X loaded to the desktop and did *not* throw up that error message about being unable to identify the hardware...  I can enable networking from a command prompt without it locking up or entering X when done.  (Got sick of running back & forth with the flash drive. ;) )

  After this, I had the thought to force grub to boot the machine to a console prompt & start X after I log in.  Searching online yielded multiple ways of accomplishing this, but none seemed to have any effect.  Did remove the 'quiet splash' parameters from the grub config file and updated; the display blanks out right after something about plymouth, but I can't tell exactly as it scrolls by and monitor goes blank in less than a second.  I'm wondering if grub is switching to a higher-than-default-resolution text mode during the boot and if that isn't what's causing the problems.  (???)  Seems to me like it blanks before X should be starting, but this is more gut feeling than anything.  How would I boot the system into a plain, ordinary text mode, if nothing else than to test whether startx from a command line after logging in works?  (Adding 'text' as a grub parameter to GRUB_CMDLINE_LINUX_DEFAULT did nothing, nor did uncommenting the 'GRUB_TERMINAL=console' and 'GRUB_GFXMODE=640x480' lines from farther down the config file.)

---

### Post by tgalati4 on 2015-05-04
Power outages can break power supplies and graphics cards need a lot of power.  So I would check the voltages in your PSU from BIOS or use a voltmeter.

---

