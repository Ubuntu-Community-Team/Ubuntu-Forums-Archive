---
title: "Ubuntu 22.04 cursor moves by itself to edge of screen, or sometimes freezes"
date: 2022-11-13
forum: General Help
---

### Post by francophone on 2022-11-13
Hello all,

I am not sure where to post this, but Ubuntu 22.04 seems super buggy. I keep discovering new issues (custom keyboard layouts don't work unless activated in the terminal, for example).

Just today, I starting having issues with the touchpad. I don't use an external mouse (I don't even have one). My cursor will randomly start moving on its own to the edge of the screen, then it will move along the edge until it goes to one of the corners. Sometimes, the pointing stick will work (but using it to move the cursor is not workable, esp. given that the cursor still has a mind of its own, and I have to compete against the cursor just to use the pointer stick). Sometimes, the cursor just freezes. I have tried restarting my laptop, but the issue persists, even on the login screen. Then it will randomly go back to normal. Rinse and repeat.

I am on a laptop and am not using multiple screens.

I know that 22.04 switched to Wayland, would that have caused it? Any ideas?

---

### Post by MAFoElffen on 2022-11-13
Have you tried the same using XServer and see if that makes a difference?

---

### Post by Raging_Cascadoo on 2022-11-13
Maybe the touchpad itself is failing. I recently had this happen on a HP laptop with similar symptoms. Even with an external mouse it was still unusable as the touchpad kept "moving" on it's own. If you have any control at all maybe try navigating to the touchpad tab under settings to disable it. I am not sure how to disable via command line, possibly with xinput I guess.

---

### Post by francophone on 2022-11-14
I don't think that it is the touchpad, I keep noticing issues with 22.04 (so much so that I am thinking about going back to 20.04, 22.04 doesn't seem stable).

I have not tried with XServer, I thought about it, but I don't know how well it will work on 22.04 (I didn't look into it either, though). But I may give it a go, I think that Wayland is my biggest complaint about 22.04, a lot of stuff doesn't act as expected.

---

### Post by Raging_Cascadoo on 2022-11-14
I can't recall where I initially got the instructions but to permanently change form wayland to xorg edit **/etc/gdm3/custom.conf **and uncomment "**#WaylandEnable=false**". I switched from wayland to xorg on both 22.04 to 22.10 without issues.

---

### Post by francophone on 2022-11-14
That's what I did, but it didn't work. Could it be a driver issue? I realized today that I have to reinstall the pilot for my printer, could the update have messed up some of the drivers on my computer as well?

---

### Post by Dennis N on 2022-11-14
> **francophone said:**
> That's what I did, but it didn't work.
Did you try choosing "Xorg on Ubuntu" at the log in screen? While the password box is open, you can select Xorg from the icon in the lower right. See screenshot.
Once selected, no need to do this on future logins. It's permanent until you deliberately change it again.

---

### Post by francophone on 2022-11-14
No, I edited the .conf file directly. I don't have that gear anyways. The issue is still ongoing.

If it is a driver issue (this problem didn't happen before the update), I don't know how I could fix it, as Toshiba/Dynabook only provides Windows drivers for my  computer.

---

### Post by Raging_Cascadoo on 2022-11-15
If it worked without issues on Ubuntu 20.04 maybe you can boot the 20.04 live environment and check if the touchpad works properly there.

---

### Post by francophone on 2022-11-15
The problem is that it is sporadic. It can happen a lot, and suddenly, or sometimes, it doesn't happen for hours and hours.

---

