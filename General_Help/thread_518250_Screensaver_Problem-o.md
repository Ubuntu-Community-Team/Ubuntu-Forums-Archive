---
title: "Screensaver Problem-o"
date: 2007-08-05
forum: General Help
---

### Post by blingboi on 2007-08-05
heres the problem, i finally found a workaround fix for my suspend problem on my laptop, before i found it I would only be able to suspend once before I either crashed or couldnt suspend anymore.

what i did was:

sudo gedit /etc/acpi/suspend.d/99-terminal-change.sh

and added 2 lines:

#!/bin/bash
/usr/bin/chvt 13

now i can suspend multiple times in a row and resume from them with no problems seen yet

however i do have this problem, i am able to see my sonar screensaver before the first suspend.... but after that when its time for the screensaver to appear, it just blanks the screen or pop up a black screen with the backlight on.

i think its because when i suspend, it puts the screensaver up for some reason, I see it when I am resuming from a suspend

is there a way to disable screensaver from popping up during the suspend process? my screen blanks out entirely when suspend is enabled, thanks for your help guys

oh yeah, all of this is done with a fresh install of feisty fawn, current updates and the radeon open source AIGLX driver

---

