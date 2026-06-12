---
title: "Ubuntu 13.04 - screen off after waking from suspend (resume)"
date: 2013-06-03
forum: General Help
---

### Post by MFritsche on 2013-06-03
Hello, 

I searched for the topic but did not find a solution. When I suspend my laptops (there are three of them), the laptop screen will not be activated on resume. I have the same behavior on a machine with 
```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
```
and with
```
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6520G]
```
so I think the graphics driver can be ruled out. I tried 
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```
in /etc/default/grub which does NOT solve the issue.

The machine can be ssh'ed in though - everything seems to be fine except that the screen won't be turned on. An external monitor will come back fine too. 

Has anyone came across the same issue and solved it?

---

### Post by ahallubuntu on 2013-06-03
It actually might be the graphics driver in both cases.

I don't use 13.04, but with 12.04 I had a similar problem with my netbook and hibernation.  (Suspend/resume worked fine.)  I found this helpful from the ArchLinux Wiki for  my netbook's chipset:

[https://wiki.archlinux.org/index.php/Poulsbo](https://wiki.archlinux.org/index.php/Poulsbo)

Page down to the section on "Fixing Suspend."  The solution of turning off the screen with xrandr before suspend (and turning it back on after resume) fixed my black screen problem after resume from hibernation.  Perhaps it will work for you with 13.04 as well.

With the Radeon, make sure you've installed the custom driver from AMD if there is one.

---

### Post by markbl on 2013-06-03
> **MFritsche said:**
> 
Has anyone came across the same issue and solved it?
On 13.04 I have a similar problem. One of my 2 desktop screens often stays blank when I return from the screensaver. The only way I get it going is by switching to a virtual console (ctrl+alt+1) and then back to X (ctrl+alt+7). Sometimes the timing of doing that sequence needs to be done just as the screen mode is changing. Try it to see if it gets around your problem.

---

### Post by hotweiss on 2013-06-10
> **MFritsche said:**
> Hello, 

I searched for the topic but did not find a solution. When I suspend my laptops (there are three of them), the laptop screen will not be activated on resume. I have the same behavior on a machine with 
```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
```
and with
```
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6520G]
```
so I think the graphics driver can be ruled out. I tried 
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```
in /etc/default/grub which does NOT solve the issue.

The machine can be ssh'ed in though - everything seems to be fine except that the screen won't be turned on. An external monitor will come back fine too. 

Has anyone came across the same issue and solved it?

The only way to fix this is to install the buggy Catalyst drivers...

---

### Post by eeslanza on 2013-06-15
hello,
i have the problem that i can suspend and resume with the discrete card  perfectly. but with the integrated card, i can susoend, but not resume, the screen stays black.
so i found that post:
[https://help.ubuntu.com//community/HybridGraphics](https://help.ubuntu.com//community/HybridGraphics) under fix suspend/wake freezing

 i created the hook file in the /etc/pm/sleep.d but 
but now i cant suspend anymore. it throws me back to the loginscreen.
i guess it has something to do with some missing permissions i dont understand.
maybe it works for you.
greetings eeslanza

---

### Post by danis2 on 2013-10-15
I came across this thread because I had a similar issue in Lubuntu 13.04. To be more specific, I had a black screen with the splash on the up left corner (followed sometimes by some characters, ie, "_@^@^@^"), and the mouse pointer was visible and functional (movable and changing to arrowhead, cursor etc). (After suspend but also sometimes when the laptop was working). I could "blindly" open the terminal and command a reboot for the blackness to vanish. Also, I couldn't return to GUI with Ctrl+Alt+F7, from the TTY, and the applications I tried to run from the TTYs where returning a "Cannot open display:" message. 

I found the solution in this how to: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

For me, it worked with the parameter nolapic.

Edit: after some use with the parameter nolapic in grub, I noticed a lower quality on my graphics and lower performance of my independent GPU, slightly slower boot time and opening of apps, and higher temperatures on motherboard.

---

