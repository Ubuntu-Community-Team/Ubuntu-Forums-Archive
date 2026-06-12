---
title: "Problem with Mouse Wheel"
date: 2007-09-03
forum: General Help
---

### Post by Gordy on 2007-09-03
I have a Logitech mouse with a wheel on it and I am so used to using it while browsing through these forums and other web sites. The problem I am having is I can scroll down the page however, when I scroll up I get a menu as if I pressed the wheel instead of moving it. This happens in Firefox only and no where else in Ubuntu 7.04...

Any ideas what I should do to fix this problem ???


I found out how to fix this problem: Click on System/Preferences/Click on Desktop Effects you know the rest...Did this and the problem went away.

---

### Post by lynrees on 2007-09-06
I have exactly the same problem. Started after kernel upgrade. I've had it before, but it went away with a kernel upgrade, but now it's back!:(

I need help before it drives me insane!!!

---

### Post by nikef on 2007-09-06
Yes i get that problem 2
rather annoying :confused:

---

### Post by steakneggs on 2007-09-15
I had the exact same problem. I did a search in the forums and found some other threads that discussed similar problems. For some reason, when I performed an update it changed my mouse settings in xorg.conf. My understanding is that the mouse keys are mapped in xorg.conf. 

Here's what it looks like on mine:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    Option	   "Buttons"	"5"
EndSection

In order to get it to work I did three things:

1) run xev to determine the numbers assigned to your mouse keys. On my system when I performed a wheel up I got button 4 and and wheel down resulted in button 5.

2) Using xev, I determined that the OS saw 5 buttons on my mouse. I added the line:
                           Option "Buttons"    "5"

I'm not sure why, but this was missing from the file.

3) I changed the line:
                          Option         "Emulate3Buttons" "true"
to
                          Option         "Emulate3Buttons" "no"

Restarting x should have done the trick but for some reason I had to reboot for it to work.

I hope this helps you!

---

