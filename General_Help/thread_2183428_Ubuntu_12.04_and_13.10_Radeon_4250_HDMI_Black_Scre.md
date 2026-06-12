---
title: "Ubuntu 12.04 and 13.10: Radeon 4250 HDMI Black Screen on Boot"
date: 2013-10-24
forum: General Help
---

### Post by mjsoccer1 on 2013-10-24
So I've been scouring the archives and forums for anyone experiencing this issue, but haven't found anyone with the exact same problem, so here goes:

- Ubuntu 12.04 HTPC is hooked up to Samsung SmartTV via HDMI
- Upon boot, I see POST, I see the blinking cursor of grub doing it's thing, I see a purple screen (plymouth?), then all goes black and TV reports "No Signal"
- PC is responsive, I can SSH, ping, etc, just no display
Here's where it gets WEIRD:
- Leaving the PC plugged into HDMI, I hooked up another monitor via DVI, and then HDMI suddenly works (but DVI monitor remains black).  I can then unplug the monitor and carry on happily using the TV as my monitor, until the next boot.

I've tried the following:
- Turn TV off, boot, then turn TV On
- Disable splash in grub [[link]("https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen")]
- Install Radeon Driver [[Link]("https://help.ubuntu.com/community/RadeonDriver")]
- Change resolution of Display in Ubuntu

All to no avail.  It would appear the the graphics card driver is working fine as after I plug in the DVI monitor and remove it, everything works and looks great.  I've even had the TV display go to sleep after not interacting with the PC, the TV reports no signal (as it should), then when I move the mouse, the display comes back.  Audio works over HDMI with no issues, but only after I perform my DVI plug/unplug trick.

I'm at my wit's end, I can't figure this out.  Note that this issue just started occurring after performing a HD swap and reinstall with 13.10- I did not have this issue at all running Ubuntu 12.04 until after my reinstall.  I still have the HD and original install on the old HD, it's just sitting in a different workstation.  I've confirmed that Grub settings are the same on this new install than with the old install.  I've since "fallen back" to Ubuntu 12.04, but this issue is still occurring.

If absolutely need be, I can pull the original drive from my other PC and boot from that to check other settings, but I'd prefer to not have to do so.  I have the drive mounted, so I can pull conf settings from it if needed.

GPU is built into the motherboard - Radeon 4250
TV is Samsung SmartTV 50"
When I got to "Display" in Ubuntu, it correctly recognizes the TV as a display

dmesg | grep 'drm|radeon' results in the following:

[SIZE=2][FONT=Courier New][    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=0c6dae95-8e8a-40ab-8be0-5452f53b93da ro radeon.audio=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=0c6dae95-8e8a-40ab-8be0-5452f53b93da ro radeon.audio=1
[    6.476770] [drm] Initialized drm 1.1.0 20060810
[    6.694062] [drm] radeon defaulting to kernel modesetting.
[    6.694066] [drm] radeon kernel modesetting enabled.
[    6.711171] [drm] initializing kernel modesetting (RS880 0x1002:0x9715 0x1849:0x9715).
[    6.711196] [drm] register mmio base: 0xFE9F0000
[    6.711197] [drm] register mmio size: 65536
[    6.711769] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    6.711771] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    6.712047] [drm] Detected VRAM RAM=256M, BAR=256M
[    6.712050] [drm] RAM width 32bits DDR
[    6.712276] [drm] radeon: 256M of VRAM memory ready
[    6.712277] [drm] radeon: 512M of GTT memory ready.
[    6.712294] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    6.713119] [drm] Loading RS780 Microcode
[    7.068766] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
[    7.068853] radeon 0000:01:05.0: WB enabled
[    7.068856] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff880115b30c00
[    7.068858] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff880115b30c0c
[    7.068860] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.068861] [drm] Driver supports precise vblank timestamp query.
[    7.068874] [drm] radeon: irq initialized.
[    7.069101] radeon 0000:01:05.0: setting latency timer to 64
[    7.100669] [drm] ring test on 0 succeeded in 1 usecs
[    7.100725] [drm] ring test on 3 succeeded in 1 usecs
[    7.100785] [drm] Enabling audio support
[    7.100803] [drm] ib test on ring 0 succeeded in 0 usecs
[    7.100816] [drm] ib test on ring 3 succeeded in 0 usecs
[    7.100973] [drm] Radeon Display Connectors
[    7.100974] [drm] Connector 0:
[    7.100975] [drm]   VGA-1
[    7.100977] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    7.100977] [drm]   Encoders:
[    7.100978] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    7.100979] [drm] Connector 1:
[    7.100980] [drm]   HDMI-A-1
[    7.100981] [drm]   HPD3
[    7.100982] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    7.100982] [drm]   Encoders:
[    7.100983] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
[    7.100999] [drm] radeon: power management initialized
[    7.117168] radeon 0000:01:05.0: No connectors reported connected with modes
[    7.117174] [drm] Cannot find any crtc or sizes - going 1024x768
[    7.123724] [drm] fb mappable at 0xD0142000
[    7.123725] [drm] vram apper at 0xD0000000
[    7.123726] [drm] size 3145728
[    7.123727] [drm] fb depth is 24
[    7.123728] [drm]    pitch is 4096
[    7.123822] fbcon: radeondrmfb (fb0) is primary device
[    7.130367] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[    7.130369] radeon 0000:01:05.0: registered panic notifier
[    7.130430] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:05.0 on minor 0[/FONT][/SIZE]

Please help!

---

### Post by zombienerd1 on 2013-10-24
I had a similar issue running through DisplayPort on my HD7770.  This was with 13.04.  IIRC, I changed the Grub resolution, and removed the splash.

In /etc/default/grub
At the bottom of the first group of settings:
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX=""


Under #The resolution used on graphical terminal
GRUB_GFXMODE=640x480

No guarantees, and no promises :)  It worked for me, and I have no issue using my Display port as primary now.

---

### Post by mjsoccer1 on 2013-10-25
Hi Zombienerd1,

Thanks for the tip.  While it appears nomodeset has fixed my black screen issue (grub resolution wasn't needed), it now looks like X/lightdm is no longer detecting my Samsung TV display, but is instead only detecting "Laptop" and only allowing a maximum resolution of 1280x1024.

Suspecting it could be a driver issue, I tried install fglrx and fglrx-updates both to no avail- it continues to detect my display as "Laptop" and I can't open the Catalyst Control Center.  When I run aticonfig --querymonitor, I get the following:

[FONT=Courier New][SIZE=2]Default Adapter - ATI Radeon HD 4250
ati_dm: X Windows is not running or $DISPLAY is not set.[/SIZE][/FONT]

xrandr returns [FONT=Courier New][SIZE=2]Can't Open Display[/SIZE][/FONT]

I failed back to the Open Source drivers as it didn't seem like I was getting anywhere with fglrx.  And am back to where I was.  If I use nomodeset, I can boot into lightdm but at a lower resolution.  If I remove the grub option, I am back to where I was where, after plugging and unplugging a monitor into the DVI port, the display appears and correctly detects my Samsung TV.

Any other thoughts?

---

### Post by Bashing-om on 2013-10-25
mjsoccer1; Hi !

Here is the deal:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <2 summers back> that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)

Which means if the proprietary drivers are required, you must run the version 12.04.1 Long Term Support. 
If you want to use the proprietary AMD/ATI driver, install Ubuntu 12.04.1 here:
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)


Else: install a "newer" graphics card that AMD supports.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by mjsoccer1 on 2013-10-25
Hi Bashing-om,

Thanks for the heads up! Explains why proprietary drivers weren't getting me anywhere.

That being said, the default open source driver appears to be working with no issues (it correctly detects the Samsung TV and supports correct resolution), but only after I hook up the DVI port to another monitor (while leaving HDMI to TV plugged in) to "jump-start" the display.  Something funky is going on with the HDMI out, which I believe I'm getting my black screen on boot issue.  

Do you know if the open source driver still supports my card (Radeon 4250)? Based upon performance, I'd say so (looks great, audio is working).  My preference is to stick with the open source driver, I was just trying the proprietary ATI to see if it'd clear up this black screen issue.

At this point, I can either use the Grub option nomodeset suggested by Zombienerd1 and avoid the black screen issue, but with sub-standard resolution, or I can boot normally then "jump-start" the display to get 1920 x 1080 and correct detection of the TV.

I just need to figure out how to get around having to "jump-start" the display to get it to output to HDMI.  Any ideas?

---

### Post by Bashing-om on 2013-10-25
mjsoccer1; Well.....

It is often amazing to me what I do not know. However,
With the open source driver, KMS (Kernel Mode Setting) is smart, real smart.
Give this a try;
Do not boot with the boot parameter:
> 
BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=0c6dae95-8e8a-40ab-8be0-5452f53b93da ro radeon.audio=1

Let the kernel figure out what it needs.
and boot to a command line interface, see what errors you see in terminal:
edit the boot parameter; remove 'radeon.audio=1' and insert the term "text" - without the quotes.
ctl+x to continue the boot process to TTY1 terminal.
Input your username and password.
Start the GUI:
```

sudo service lightdm start ## assuming you are running a standard DE

```
Best I recall now you should be at the GUI login. yes ? .. log in and advise on what the graphics look like.
to revert back to TTY1 -> ctl_alt+f1, GUI -> ctl+alt+f7
No GUI ?
to reboot: Terminal code:
```

sudo shutdown -r now
##to shutdown gracefully and power off:
sudo shutdown - P now

```

[INDENT][INDENT]ubuntu, many roads lead to one end
[/INDENT][/INDENT]

---

### Post by mjsoccer1 on 2013-10-26
Thanks Bashing-om for the suggestion, however I still experienced the same issue when booting without the radeon.audio boot parameter and into text/runlevel 3/no lightdm.  After performing my "jump-start" using the DVI connection, I was able to login and start lightdm with no problems, although audio via HDMI wasn't working.

BUT, I have worked out the problem! The issue appears to be my HDMI cable.  On the hunch that the PC just wasnt detecting any power on the GPU (since plugging in a powered monitor the DVI port would "jump-start" it), I swapped out for a different HDMI cable and sure enough all is up and working now- I can boot into lightdm/runlevel 5 with no black screen issues!

Definitely an odd issue, particularly because the boot parameter domoreset worked around the issue and for the fact that I've been using this HDMI cable with this PC and Ubuntu 12.04 for nearly two years.  Perhaps the cable got tweaked while removing the HTPC case to swap out hard drives?  No matter the reason, I'm all set up and running!

The next question is should I now upgrade from 12.04 LTS to 13.10? :-)

Thank you to Zombienerd1 and Bashing-om or the helpful suggestions!

---

### Post by Bashing-om on 2013-10-26
mjsoccer1; Outstanding, Glad there is resolution.
All I can surmise is with the "weak" cable the system was not detecting the EDID info from the monitor.
Please mark this thread as solved -> 1st post -> thread tools.

As to up-grading to 13.10. That is a personal choice. 12.04 is THE stable Long Term Support, good 'till 2017. Versions 13.10 ^ are the "testing" and have the latest and greatest but may also have problems. Also one has the responsibility - that one should exercise anyway - of keeping the system backed up in preparation  for the 9 month upgrade cycles.

My choice is to triple boot 'buntus. I have my "work" install as a minimal 13.04, my "play" as ubuntu 12.04, and "testing" as latest Lubuntu version.
My 12.04 ubuntu as the stable backup for any contingency. I do keep good backups ! I have learned the hard way, I do not like loosing my data to dumb-ass attacks !

Keep on keep'n on
[INDENT][INDENT]enjoy ubuntu !
[/INDENT][/INDENT]

---

### Post by mjsoccer1 on 2013-11-03
Thread reset to "Unresolved".  Note that this problem is exasperated by the latest kernel upgrade on 12.04 LTS- Issue does not appear when booting to kernel 3.8.0-28, however kernel 3.8.0-32 results in no HDMI output.

When booting to 3.8.0-32, I can see up to the point of grub menu, then black screen.  Unlike before, now connecting another monitor to the DVI port does nothing (no "jump-start").

Temporary workaround is to continue to boot to older kernel:
[FONT=Courier New]sudo vi /etc/default/grub:

GRUB_DEFAULT="2>0"

sudo update grub[/FONT].

Given current behavior, it would appear the issue is driven by the kernel.  Any additional thoughts? Should I log a bug report and upload dmesg/logs? Thanks!

---

### Post by mjsoccer1 on 2013-11-03
Xorg.0.log output when booting to 3.8.0-32:

[INDENT][FONT=Courier New]X.Org X Server 1.13.3
Release Date: 2013-03-07
[    12.956] X Protocol Version 11, Revision 0
[    12.956] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    12.956] Current Operating System: Linux seppotv 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64
[    12.956] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-32-generic root=UUID=0c6dae95-8e8a-40ab-8be0-5452f53b93da ro
[    12.956] Build Date: 16 October 2013  04:46:41PM
[    12.956] xorg-server 2:1.13.3-0ubuntu6~precise3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    12.956] Current version of pixman: 0.24.4
[    12.956] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    12.956] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.957] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  3 08:25:57 2013
[    12.973] (==) Using config file: "/etc/X11/xorg.conf"
[    12.973] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.006] (==) No Layout section.  Using the first Screen section.
[    13.006] (**) |-->Screen "Default Screen" (0)
[    13.006] (**) |   |-->Monitor "<default monitor>"
[    13.006] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    13.006] (==) Automatically adding devices
[    13.006] (==) Automatically enabling devices
[    13.006] (==) Automatically adding GPU devices
[    13.078] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.078] 	Entry deleted from font path.
[    13.078] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.078] 	Entry deleted from font path.
[    13.078] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.078] 	Entry deleted from font path.
[    13.078] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.078] 	Entry deleted from font path.
[    13.078] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.078] 	Entry deleted from font path.
[    13.078] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    13.078] 	Entry deleted from font path.
[    13.078] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    13.078] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.078] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.078] (II) Loader magic: 0x7f472d420c20
[    13.078] (II) Module ABI versions:
[    13.078] 	X.Org ANSI C Emulation: 0.4
[    13.078] 	X.Org Video Driver: 13.1
[    13.078] 	X.Org XInput driver : 18.0
[    13.078] 	X.Org Server Extension : 7.0
[    13.079] (II) config/udev: Adding drm device (/dev/dri/card0)
[    13.080] (--) PCI:*(0:1:5:0) 1002:9715:1849:9715 rev 0, Mem @ 0xd0000000/268435456, 0xfe9f0000/65536, 0xfe800000/1048576, I/O @ 0x0000d000/256
[    13.080] (II) Open ACPI successful (/var/run/acpid.socket)[/FONT][/INDENT]

---

