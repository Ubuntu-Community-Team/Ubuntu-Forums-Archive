---
title: "WiFi and touchpad issues"
date: 2015-03-21
forum: General Help
---

### Post by eva6 on 2015-03-21
Hi all,

So i just installed 14.04 which is my first version of Ubuntu, and I was wondering why my mouse cursor (the little white arrow, I don't know how else to call it) is constantly flickering (disappearing then reappearing again) and sometimes disappearing completely;

Also I have a very long WiFi password, is there a way to store it so I don't need to type it in everytime I use my computer?

Thanks!

---

### Post by gordintoronto on 2015-03-21
You should not need to enter your Wi-Fi password every time.

As for the mouse cursor, you should tell us the brand and model of computer. Does the problem happen when you use an actual mouse?

---

### Post by eva6 on 2015-03-28
Hi, thanks for answering,
The wifi issue seems to have solved itself on its own.
As for the cursor, my laptop is an Asus X53S, and plugging a mouse in does not change anything (Sometimes the cursor also leaves a "ghost" in the middle of my screen, a copy of itself that I can't remove without restarting my PC...). What could it be?
Thanks,
Eva

---

### Post by Vladlenin5000 on 2015-03-28
Asus X535 has a ```
**Graphics Adapter:** [NVIDIA GeForce GT 520MX]("http://www.notebookcheck.net/NVIDIA-GeForce-GT-520MX.54717.0.html")
``` which probably needs proprietary nvidia drivers to work properly.

---

### Post by eva6 on 2015-03-29
Oh, ok... Any idea where I could get those? Pardon my question but I'm very much a noob ^^
(For the record, I partitioned my drive so I still have the old Windows 7, could that be of any help?)

---

### Post by Vladlenin5000 on 2015-03-29
Intro:
Windows isn't required but there's no problem in having it. It's often recommended for easy BIOS/UEFI updates - many vendors still package those updates in Windows executable programs/installers (*.exe) - and it helps in troubleshooting hardware issues (when something doesn't work in Linux but it does in Windows we know it's a software/drivers issue). 

Nvidia drivers:
Several options but it's recommended to use the easiest method. System Settings > Software & Updates. Now find and open the rightmost tab "Additional drivers"; wait a few moments and the system should bring you a list of suggestions. In that list you'll see that *nouveau*, the community open source driver is selected and in use (it's the default). Now you can select and apply the recommended proprietary driver, probably the 331-(something). Wait for the process then reboot. If you see a different, less appealing Ubuntu splash screen (wrong resolution and verbose), that's indicative of the new driver in use.
Test the system as usual. If it works as expected then keep it; if not you can try more recent drivers with a different method.
Obs.: The splash screen is an unfortunate side effect of the proprietary drivers. There are a few solutions for that too but it isn't a problem *per se*, the resolution and overall aspect at login and in a session should be fine,

---

### Post by eva6 on 2015-04-07
Hi, thanks all for your help! turns out I just had to go into System Settings > Display and then disable Unknown Display. Just posting this in case someone else has the same issue.

---

