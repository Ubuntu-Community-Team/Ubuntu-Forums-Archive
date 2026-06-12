---
title: "Computer Fan Not Working Properly"
date: 2016-04-25
forum: General Help
---

### Post by Zevidrex on 2016-04-25
I own a Yoga Thinkpad that runs ubuntu 16.04. This issue was on previous versions of ubuntu however. My computer gets hot. My fan is working...ish. When it gets hot, instead of kicking into high gear, the computer does not kick into any gear at all except the bare minimum gear. We even verified this when me and my linux savvy friend found out that its running on level 0. When typing in [FONT=monospace][COLOR=#000000]echo level 7 > /proc/acpi/ibm/fan i[/COLOR][/FONT]nto the terminal as root, the error message [FONT=monospace][COLOR=#000000]-su: echo: write error: Invalid argument [/COLOR][/FONT]pops up. We did something else but got the same error. We even tried to put a command into the startup script to get the fan blazing, but all we got was the same silent whir. The fan seems to be working but it isnt programmed to do anything else. It might have to do with the thermal sensor but the fan should have responded to the commands. What I want is the ability to manually turn the fan on personally. Anybody want to help?[FONT=monospace]
[/FONT]

---

