---
title: "Laptop will not awake after suspend but LEDs on keyboard and back remain on and fans"
date: 2016-03-05
forum: General Help
---

### Post by karan9 on 2016-03-05
[TABLE]
[TR]
[TD]

[/TD]
[TD]I'm currently running Ubuntu 15.10 on my razer blade 2015 and cannot get the suspend feature to work properly. When I press the suspend button or close the lid, the LEDs on the keyboard and back remain on and the fan turns on. I cannot get the screen to resume/turn on and have to force shutdown and reboot. Although pressing the power button while the screen is black seems to power up the fans. I do not think this is a graphics driver issue since I have tried various drivers and my intel graphics with no success.
I think it may be an ACPI issue. Additionally, when I have lid closing set to do nothing, and I close my lid, the lid indicator gets stuck on closed.

XX@XX-Blade:~$ cat /proc/acpi/button/lid/LID0/state 
state: closed

My graphics is a 970m running the nvidia-352 although I have selected to use my intel graphics from prime profile. 
Here is my suspend log: pastebin.com/Mq8XqDGv[/TD]
[/TR]
[/TABLE]

---

