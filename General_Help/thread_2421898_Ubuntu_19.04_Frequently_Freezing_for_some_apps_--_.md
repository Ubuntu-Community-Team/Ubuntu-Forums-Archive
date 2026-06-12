---
title: "Ubuntu 19.04 Frequently Freezing for some apps -- seems amdgpu related"
date: 2019-06-28
forum: General Help
---

### Post by alvin2 on 2019-06-28
System is crashing repeatedly when using SOME applications, unfortunately Jetbrains software is one of the culprits and necessary for me work

Been running an AMD Radeon RX 570 based video card for a couple years, previous to 19.04 I was running the amdgpu-pro proprietary drivers.

Tried upgrading, had issues with stability almost immediately
Fresh install twice, same thing

Currently running amdgpu open source drivers, they're proving more stable that proprietary but not by much...

user level details:[INDENT]System is stable when left alone, disabled suspend and let it run for 2 days left alone no issue
Usage of Jetbrains software / spotify / several others results in a crash within a few minutes, where screens turn gray/black -- CTRL+ALT+F{x} fails, can't SSH in from an outside computer
Usage of ATOM / chrome / terminator and a few others installed through `apt` does not cause issue
this is not heat related system was rock solid on 17.10 / 18.04 / 18.10[/INDENT]

Reports from the internet suggest this is related to snap packages, though I'm unsure if I wanna dive down installing gnome-shell outside of snap since that's now the expected configuration


System details:

```
sudo lshw -C video                                                                                                         &#57522; &#10003; 

  *-display                 
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: c7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:58 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fe800000-fe83ffff memory:c0000-dffff

```

```
ls -alt /var/crash                                                                                                         &#57522; &#10003; 
total 49252
drwxrwsrwt  2 root     whoopsie     4096 Jun 28 16:53 .
-rw-------  1 whoopsie whoopsie       37 Jun 28 16:22 _usr_bin_gnome-shell.1000.uploaded
-rw-r-----  1 alvin    whoopsie 50421573 Jun 28 16:22 _usr_bin_gnome-shell.1000.crash
-rw-r--r--  1 alvin    whoopsie        0 Jun 28 16:22 _usr_bin_gnome-shell.1000.upload

```

Checking through syslog / dmesg isn't turning up much that seems relevant but I may not be greping for the right stuff


Any other info can I share to help debug?


Hoping someone can point me towards a breadcrumb to solve, can't work when the system halts every few minutes :(
Nearly ready to just buy a NVIDIA card and cross my fingers

---

### Post by #&amp;thj^% on 2019-06-28
**Not to sway you any way shape or form, Nvidia for me is very very stable.**
Hope someone helps you first though.

---

### Post by alvin2 on 2019-07-01
1fallen -- are you running ubuntu 19.04?
open source or propietary drivers?

Over the years I've switched back and forth between video card providers for issues similar to this -- it sucks but it's also part of the trade off for open source software and I understand that

---

### Post by QIII on 2019-07-01
> **1fallen said:**
> Not to sway you any way shape or form, Nvidia for me is very very stable.

And AMD products have been very stable for me.

@alvin2 --

What leads you to believe the issue seems to have anything to do with your graphics driver.  You said yourself that your research seems to indicate something about a snap.

Just to clarify:  there is not a separate open source AMDGPU driver differentiated from a proprietary one.  AMDGPU is open source.  Even if you have AMDGPU-PRO installed, you are still using AMDGPU.  PRO is simply an overlay of additional proprietary functionality on top of AMDGPU.

---

### Post by #&amp;thj^% on 2019-07-01
> **alvin2 said:**
> 1fallen -- are you running ubuntu 19.04?
open source or propietary drivers?

Over the years I've switched back and forth between video card providers for issues similar to this -- it sucks but it's also part of the trade off for open source software and I understand that

Yep and 18.04, and 19.10. But for my Thinkpads I opted to not buy with hybrid cards, went strictly Intel and opensource.
My Nvidia card is using proprietary driver on a dedicated tower.
FTR: I don't install Gnome Shell (No More interest), or snapd.
Might not hurt to take a look at:
```
systemctl --failed
```

---

### Post by alvin2 on 2019-07-01
Didn't take the best notes while I was diving into all this but there are a few references to AMD cards being unstable with snap packages

 - quick search through history shows this one [https://cialu.net/how-to-solve-crash-issue-amdgpu-pro-linux-driver-ubuntu/](https://cialu.net/how-to-solve-crash-issue-amdgpu-pro-linux-driver-ubuntu/)
    there are more references that I read through and tried different paths to debug -- near certain about the AMD + SNAP being the culprit but would love to find I'm wrong and it's actually something simple

good to know about AMDGPU vs AMDGPUPRO -- they used to be separate but I haven't been keeping track of updates in that realm for a few years

next time I have a freeze I'll post an output of `systemctl --failed`

thank you

---

### Post by alvin2 on 2019-07-01
output from ```
systemctl --failed
``` is unfortunately not helpful on a fresh boot

```
systemctl --failed                                                                                                         &#57522;&#10003;
0 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.
```

will parse the archived syslog and share later if useful

output from systemctl list-unit-files is over 200 lines so I'll save posting that unless it'll be useful

---

### Post by alvin2 on 2019-07-11
UPDATE: swapped out with a nvidia card -- hasn't frozen since...

pretty sure the root cause is related to isolated drivers in snap -- gnome-shell being installed through snap now makes it difficult to just remove the management system...

if anyone has an idea for how to debug I still have the AMD card and willing to put in some time to narrow it down but otherwise back to work

many thanks

---

### Post by deadflowr on 2019-07-12
> **alvin2 said:**
> 

pretty sure the root cause is related to isolated drivers in snap -- gnome-shell being installed through snap now makes it difficult to just remove the management system...



What do you mean by snap?
Snap packages?
If that's the case, then nope.
gnome shell has never been a snap on Ubuntu.
(there may be snap package or two someone published, but Ubuntu has never shipped the desktop as one)
Gnome Shell on Ubuntu is the genuine traditional article.

---

### Post by freebird54 on 2019-07-12
No expertise here - but is there any chance that wayland crept into use on your system? You could check the 'cog' at your next login to be sure - or
```

echo $XDG_SESSION_TYPE

```
should tell you. Had a few surprises on my Vega11 graphics that way...

freebird

---

