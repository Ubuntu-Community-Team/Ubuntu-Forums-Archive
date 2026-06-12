---
title: "Ubuntu 22.04 Deskop freezing"
date: 2023-04-25
forum: General Help
---

### Post by nasturtium2 on 2023-04-25
My computer keeps randomly freezing where the desktop completely hangs and the keyboard and mouse are unresponsive. It will not respond to opening a new terminal with CTRL+ALT+F2 or a REISUB. I have scoured the forums and seems like the most related issue people are reporting comes with a GPU hang reported in the syslog or dmsg. Unfortunately I do not see an clear reports of a GPU hang in my syslog or dmesg. 

So far all I have tried is a sudo apt update and sudo apt upgrade. Updated the BIOS on the machine (and my thinkpad thunderbolt 3 dock). 

Any suggestions to find out what is causing the crash?

Specs:

Lenovo ThinkPad T14 Gen 2i
Processor: 11th Gen Intel® Core™ i5-1135G7 @ 2.40GHz × 8
Graphics: Mesa Intel® Xe Graphics (TGL GT2)
Graphics Driver: i915
Ubuntu 22.04.2 LTS
64-bit
GNOME ver.: 42.5
Windowing: X11

---

### Post by emrys on 2023-07-25
Same thing happening here sice a week or two ago. The only way to recover is a hard shutdown :(

Saw some Nvidia errors in the logs, upgraded to the new proprietary tested 535 Nvidia drivers, but still seeing the issue.

---

### Post by superuserdoo on 2023-10-21
I would love an answer to this thread as well, same exact issue and I have Mesa Intel® Xe Graphics (TGL GT2) graphics card as well. Have yall found an answer yet?

---

### Post by jdefed on 2023-10-22
I've had this problem for a couple of months, when my kernel updated to 6.xxx. If I run 5.19 I don't have the problem. So for now I just run 5.19.

---

### Post by MAFoElffen on 2023-10-23
@superuserdoo & jdefed -- Please start a new thread on Intel XE Graphics and the 6.X kernels. 

This thread was last active April 2023. The OP is not following it any longer and things have changed since then.

I also have been working with the Intel Support Engineers on this, and they owe me answers (which I need to fire off an email to them this morning!!!)

---

### Post by vmpx on 2023-11-06
I use in 20.04 the parameter "nomodeset" in GRUB menu.

---

