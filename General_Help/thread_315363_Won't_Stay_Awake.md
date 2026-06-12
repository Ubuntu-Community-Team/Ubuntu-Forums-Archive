---
title: "Won't Stay Awake"
date: 2006-12-09
forum: General Help
---

### Post by Ephilei on 2006-12-09
I just did a fresh install of Edgy and it will ignore the Power Management GUI set to never suspend. I've tried appending /etc/X11/xorg.conf with the following

```
Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection
```

but there's no effect. I use the computer as a server, so this is a pretty big deal.

---

### Post by m83 on 2006-12-09
Try adding [FONT="Courier New"]Option "NoPM" "yes"[/FONT] to the "ServerFlags" section and disabling [FONT="Courier New"]Option "DPMS"[/FONT] in the "Monitor" section.

---

### Post by Ephilei on 2006-12-09
OK, I'll try that.

---

### Post by Ephilei on 2006-12-09
Nope. Still no affect whatsoever.

---

### Post by Ephilei on 2006-12-09
Where's the suspend script? Can't I just replace the contents with an empty script?

---

### Post by Ephilei on 2006-12-11
Tried some fidgeting. This page helped ([http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)) but nothing worked. I ran 

xset -dpms

which should completely disable dpms but the system still acts as normal.

---

### Post by m83 on 2006-12-11
Try looking in System->Preferences->Power Management and System->Preferences->Screensaver (stop the screensaver or disable anything that you think can black the monitor).

---

### Post by Ephilei on 2006-12-11
Yeah, I already disabled all those values. That was the first thing I tried.

---

### Post by Ephilei on 2006-12-11
By the way the system also suspends when I'm actively using remote desktop. Is idleness determined only by physical inputs (mouse, keyboard)? Is there a way to simulate a physical input?

I don't think it has anything to do with dpms because dpms regulates the monitor but the whole system is suspending.

---

### Post by wpshooter on 2006-12-11
First make sure that you have the button marked in the **SESSIONS** section so that changes to your sessions are automatically saved when you do a restart or shutdown.

Set your screen saver setting to ON and to kick in at 2 minutes and then set the power management for the screen to blank to 3 mintues.

Let them work.  First the screen saver and then the screen will blank after one more minute.

Then reboot system.

Then go into the screen saver section and turn the screen saver function OFF but do **NOT** move the setting from the 2 minutes setting that you just previously set it to.

Then go into the power management section and slide the setting to never.

Then wait for about 10 minutes to see that the screen does not go blank.  Then restart the machine.  After getting back up see if the machine does not go blank.

Good luck.

---

### Post by Ephilei on 2006-12-12
Thanks. I'll try that. It sounds really stretched, tho. What's the logic behind it?

---

### Post by Ephilei on 2006-12-12
It appears I might have a bug in my sessions manager too (great!), nevertheless the computer still suspends before rebooting as well as afterwards.

wpshooter - are you just messing with me?

---

### Post by Ephilei on 2007-04-23
OK, I finally stumbled upon the answer: the BIOS. The BIOS has a suspend setting that overrides Ubuntu.

BTW, I managed to successfully break the suspension by giving continuous input to the keyboard for about ten hours. I placed a heavy object on the keyboard. I don't, however, know why that worked.

---

