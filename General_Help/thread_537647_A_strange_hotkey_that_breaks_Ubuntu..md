---
title: "A strange hotkey that breaks Ubuntu."
date: 2007-08-29
forum: General Help
---

### Post by Jakevn on 2007-08-29
I had been using Wine earlier and wanted to exit the window but since I am only used to OSX and Win key maps, I was reduced to guessing. This ended up in me finding the "Screw up Ubuntu" hotkey. X shut down and I was at the CLI login. I typed startx and was back to the Gnome desktop. Everything seemed fine at first but now my camera is no longer recognized when I connect it, the laptop will no longer suspend when the lid is closed, and I have to manually startx every time I boot. Why did this happen and how can I fix it? :confused:

 Any help is much appreciated.

---

### Post by PilotJLR on 2007-08-29
Did you press Ctrl + Alt + FunctionKey? Cause that it supposed to happen.

If it does, then Ctrl + Alt +F7 takes you back to X. I would recommend logging off and then doing that, since now you have 2 X sessions running at the same time.

EDIT: Sorry - disregard... I see you already rebooted.

---

### Post by Jakevn on 2007-08-29
Yeah, I could see a hotkey that shuts down the X server but I don't quite understand why it no longer starts on a cold boot. I don't know why my camera is no longer auto-detected or why it will no longer suspend when the lid is closed either. :(

Edit: Forgot to add, I didn't make any system changes or install any programs during this session, and my camera/suspend was working during this session prior to the incident.

---

### Post by soxs on 2007-08-29
Do remember at least parts of your *killer*-key-combo? Maybe we can recover the key-combo completly and so reverse the process...

---

### Post by Jakevn on 2007-08-29
Unfortunately I don't, but I have a feeling that it was ctrl + alt + one of the F keys, meaning I most likely switched to a virtual terminal. At which point I used startx, realized my camera wasn't working and power states weren't working, then rebooted. It doesn't explain the fact that X doesn't start when I cold boot or why my camera and power states aren't working.

---

### Post by Jakevn on 2007-08-29
:popcorn:

---

### Post by Jakevn on 2007-08-29
Also, I must add that there is no longer a shut down option in the Quit menu.

Edit: Found the problem. Apparently gdm was completely missing. Reinstalled it and everything is working fine now.

I'm speechless.

---

