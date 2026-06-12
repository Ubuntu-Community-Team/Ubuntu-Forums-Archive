---
title: "Can't seem to get 'Energy Star' timeout to work for my monitor"
date: 2022-04-04
forum: General Help
---

### Post by lelandiniowa on 2022-04-04
For some reason I can't seem to get 'Energy Star' to work for my monitor.

If I enter:[INDENT]xset dpsm force off[/INDENT]
my monitor turns completely off as expected, so the PC seems capable of turning the monitor off, but if I enter something like:[INDENT]xset dpsm 300 300 300
[/INDENT]
my monitor doesn't ever actually turn off. The screen is blanked but the backlight is still on. Entering 'xset q' indicates that DPMS is set as I expected:[INDENT]DPMS (Energy Star):[/INDENT]
[INDENT]  Standby: 300    Suspend: 300    Off: 300[/INDENT]
[INDENT]  DPMS is Enabled[/INDENT]
[INDENT]  Monitor is On[/INDENT]
'xset q' also lists this for the screen saver settings:[INDENT]Screen Saver:[/INDENT]
[INDENT]  prefer blanking:  yes    allow exposures:  yes[/INDENT]
[INDENT]  timeout:  0    cycle:  0[/INDENT]
I tried setting 'xset x noblank' but that didn't make any difference. In other words, the screen is still blanked but the backlight is still on, so the monitor didn't actually turn off.

Is there some other setting for DPMS (Energy Star) that I'm missing? It just seems very odd that I can force the monitor to turn off but I can't seem to get the timeout to work.

The versions for my installation are: Ubuntu 20.02.4, 64-bit, Gnome 3.36.8, X11 Windowing System. 
My PC is as follows: Memory 31.2 GiB, Processor Intel Core i7-8559U CPU @ 2.70 GHz x 8, Graphics Mesa Intel Iris Plus Graphics 655 (CFL GT3), Disk Capacity 1.0 TB.
My Monitor is an acer 4K monitor connected via HDMI.

---

### Post by #&amp;thj^% on 2022-04-04
Have a look here: [https://wiki.archlinux.org/title/Display_Power_Management_Signaling#Setting_up_DPMS_in_X](https://wiki.archlinux.org/title/Display_Power_Management_Signaling#Setting_up_DPMS_in_X)

Examples:
```
Command 	Description
xset s off 	Disable screen saver blanking
xset s 3600 3600 	Change blank time to 1 hour
xset -dpms 	Turn off DPMS
xset s off -dpms 	Disable DPMS and prevent screen from blanking
xset dpms force off 	Turn off screen immediately
xset dpms force standby 	Standby screen
xset dpms force suspend 	Suspend screen
```

To query the current settings:

```
$ xset q
```
Mine is disabled:
```
DPMS (Energy Star):
  Standby: 600    Suspend: 600    Off: 600
 **[COLOR="#FF0000"] DPMS is Disabled[/COLOR]**

```

---

### Post by lelandiniowa on 2022-04-04
Thanks for the reply but, as I explained in my original post, I knew what those commands were.

 The link you provided mentions 'a file in /etc/X11/xorg.conf.d/ in the Monitor section' but there is no such directory on my installation. So it isn't clear to me where to make the changes mentioned in the article. I tried to grep everything in the /etc/X11/ directory for 'OffTime' but it didn't find anything.

I originally tried: 'xset dpms 300 600 900'.

When I noticed a few hours later that the backlight on my monitor display was still on (indicating that the monitor display wasn't actually off), I started trying other settings.

'xset dpms force off' immediately blanks the screen and also turns off the backlight on the monitor display but 'xset dpms xxx xxx xxx' (with the timeout values) blanks the screen but never turns off the backlight on the monitor display.

Using the screen saver settings 'xset s xxx xxx' also blanks the screen but never turns off the backlight on the monitor display.

If the backlight on the monitor display is still on, it isn't actually saving any energy, which is supposed to be the purpose of DPMS. So, it seems to me that there is a bug in the 'xset dpms' command when using the timeout values but I don't know how to verify or report that.

---

### Post by #&amp;thj^% on 2022-04-04
Ah that's a better explanation.
Sadly The issue still exists after a fresh install of 21.10 and going forward to 22.04
A regression or a bug, IJDK
but there is a discussion about it here: [https://community.acer.com/en/discussion/632743/vg280k-backlight-turns-on-and-off-forever-via-displayport-when-monitor-sleeps](https://community.acer.com/en/discussion/632743/vg280k-backlight-turns-on-and-off-forever-via-displayport-when-monitor-sleeps)

---

### Post by #&amp;thj^% on 2022-04-04
> **lelandiniowa said:**
> 
 The link you provided mentions 'a file in /etc/X11/xorg.conf.d/ in the Monitor section' but there is no such directory on my installation. So it isn't clear to me where to make the changes mentioned in the article. I tried to grep everything in the /etc/X11/ directory for 'OffTime' but it didn't find anything.



You would have to create that file: "Note: As of Xorg 1.8 DPMS is auto detected and enabled if ACPI is also enabled at kernel runtime.
EDIT: as an example:
```
sudo dmesg | grep ACPI
[sudo] password for me: 
[    5.591355] ACPI: AC: AC Adapter [ADP0] (on-line)
[    5.650049] ACPI Warning: \_SB.PCI0.GPP0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20210930/nsarguments-61)
[    5.683445] ACPI: video: [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    5.684612] ACPI: video: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[    5.689835] ACPI: video: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    5.689907] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.GP17.VGA.LCD._BCM.AFN7], AE_NOT_FOUND (20210930/psargs-330)
[    5.689913] ACPI Error: Aborting method \_SB.PCI0.GP17.VGA.LCD._BCM due to previous error (AE_NOT_FOUND) (20210930/psparse-529)
[    5.689919] ACPI: \_SB_.PCI0.GP17.VGA_.LCD_: _BCM evaluation failed
[    5.855865] ACPI: battery: Slot [BAT0] (battery present)

```

Add the following to a file in /etc/X11/xorg.conf.d/ in the Monitor section: "
So an example of that would look like: /etc/X11/xorg.conf.d/10-monitor.conf
```
Section "Monitor"
    Identifier "LVDS0"
    Option "DPMS" "false"
EndSection

Section "ServerFlags"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
    Option "BlankTime" "0"
EndSection

Section "ServerLayout"
    Identifier "ServerLayout0"
EndSection

```
what did your query show? **"xset -q"**

---

### Post by lelandiniowa on 2022-04-04
Thanks. That discussion is similar to what I see but the backlight doesn't alternate off and on as in that discussion. There is some slightly different behavior for me (the monitor cycles through inputs for awhile, then the screen unblanks). That happens for awhile, then the screen eventually blanks permanently (but the backlight still remains on). 

In any case, it sounds like it may be a problem with my acer monitor so I'll have to ask acer about it.

---

### Post by lelandiniowa on 2022-04-04
> **1fallen said:**
> 
what did your query show? **"xset -q"**

Sorry, I hadn't figured out how to identify something as code in my original post, so you apparently missed it.

```

Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
DPMS (Energy Star):
  Standby: 300    Suspend: 300    Off: 300
  DPMS is Enabled
  Monitor is On

```

---

### Post by #&amp;thj^% on 2022-04-04
You could try that edit to /etc/X11/xorg.conf.d and save your as: "**10-monitor.conf**"
I'd be curious if it works, i have about an 80% success in my test rigs. (I have not used your monitor though in my rigs)
Acer and I kind of had a falling out.(Useless to the post)

---

### Post by lelandiniowa on 2022-04-05
I did get that file created and added to that directory. Do I need to do chmod +x for the file? Also, do I need to restart anything for it to be recognized?

This is the first acer product I've ever purchased, so I've no previous experience with the brand. This monitor was the only one I found that had the features I was looking for, so I tried it.

---

### Post by #&amp;thj^% on 2022-04-05
> **lelandiniowa said:**
> I did get that file created and added to that directory. Do I need to do chmod +x for the file? Also, do I need to restart anything for it to be recognized?

This is the first acer product I've ever purchased, so I've no previous experience with the brand. This monitor was the only one I found that had the features I was looking for, so I tried it.

Nope nothing else needed, just a reboot to kick it in. (If it will work)
Let us know would ya? :)

---

