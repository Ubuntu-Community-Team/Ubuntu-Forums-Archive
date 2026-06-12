---
title: "Random Shutdowns, then Boot Problem - I'm Stumped"
date: 2024-06-26
forum: General Help
---

### Post by drumone on 2024-06-26
I'm running Ubuntu 22.04.4 LTS on a custom system that I built 2.5 years ago. It has operated normally up until recently. I'm stumped as to the cause and resolution of this issue.

Problem: 
The OS randomly shuts down for no apparent reason. It only occurs when I am away from my computer, never while I'm using it. When I come back to the system to find it off, it won't reboot. I have to manually shut off the power and then turn it back on for it to start up again. Usually I just flip the switch on the power module, but it works if I turn off the power strip as well. Everything about this is completely random! Sometimes it does it, sometimes it doesn't. The programs I have running at the time make no difference. The time away from the system makes no difference. I can't figure out any sort of pattern or commonality to any if this. 

Does anyone have any ideas as to what could be going on? Short of dropping the case out the window, I'm willing to try just about anything.

System Specs:
Asus ROG Crosshair VIII Dark Hero AMD X570 ATX motherboard
AMD Ryzen 9 5950x processor
  Arctic Liquid Freezer II 360 CPU cooler &#8211; front mounted
Asus Dual-RX6600 GPU
  G.Skil RipJaws V 64GB RAM
  Samsung 980 Pro SSD &#8211; 1TB NVMe - Ubuntu
  Samsung 980 Pro SSD &#8211; 1TB NVMe - Windows
  Corsair RM850x power supply
  Fractal Design Pop XL Air ATX Full tower case
  Fractal Aspect 12 120mm case fan &#8211; 2 in the top, 1 in the rear

---

### Post by dragonfly41 on 2024-06-26
> [COLOR=#000000]It only occurs when I am away from my computer, never while I'm using it[/COLOR][COLOR=#000000]

An intriguing puzzle. Do you perchance have a webcam attached?
what I would try out of curiosity is a script which keeps moving the cursor around randomly (while you are away) to see if this breaks the code. Actiona does that but also [xdotool.]("https://github.com/jordansissel/xdotool")[/COLOR]

---

### Post by him610 on 2024-06-26
I have no idea what the cause of your problem is; however, you should consider the possibility that some of you assemblies/components do not play well together. 
I have seen at least one instance where a power supply (with symptoms similar to yours) would not work consistently with a certain motherboard - fixed by replacing PSU. I have also seen issues with memory/cpu/motherboard combinations. I have seen problems with overheated CPUs; although, that normally shuts your computer completely down.

Scour the internet for issues with each one of your system components. You may discover something.
Check the logs.

---

### Post by dragonfly41 on 2024-06-27
From the clues given this seems to be linked to "presence" at desktop.
Odd theory, I know. But can you try a different mouse to eliminate everything related to "presence" (webcam/mouse). i have read of stranger things such as pets pulling plugs.  Monitor keyboard/mouse usage while you are "away". Kids playing? Lock access while you are "away".

---

### Post by currentshaft on 2024-06-27
> **drumone said:**
> The OS randomly shuts down for no apparent reason. It only occurs when I am away from my computer, never while I'm using it. When I come back to the system to find it off, it won't reboot. I have to manually shut off the power and then turn it back on for it to start up again. Usually I just flip the switch on the power module, but it works if I turn off the power strip as well. Everything about this is completely random! Sometimes it does it, sometimes it doesn't. The programs I have running at the time make no difference. The time away from the system makes no difference. I can't figure out any sort of pattern or commonality to any if this.

I don't understand. You find it off, but then you power it off? Then it's not off, is it?

Have you tried turning off sleep/suspend?

Have you tried updating the BIOS/EC firmware?

Have you looked at /var/log to find messages from around the time the computer was left unattended?

---

