---
title: "Krita Freezes when Wacom pen touches tablet"
date: 2023-11-09
forum: General Help
---

### Post by heimerdinger123 on 2023-11-09
Hey folks,
as the the title already says, I have a problem with krita. Everything is fine with the tablet and inputs. I can use it for other applications and in general for navigating on the desktop etc. But as soon as I want to do any input with the tip of the pen in Krita it freezes and nothing happens. I can undo the freeze by hitting the win-key, but when I go for it again the same problem appears again. I already searched the web for a solution but didn't find any.
Any help is appreciated!

---

### Post by treeert on 2023-11-11
Hi Heimerdinger123, hi all,
I have the same problem and it's not actually exclusively happening in Krita but also Blender and GIMP. I tried to reinstall libinput and the wacom drivers but nothing seems to help so far.

---

### Post by treeert on 2023-11-12
After some more research and digging, the tablet now works again. 
I just completely removed the xserver-xorg-input-wacom package, and after a restart and a reinstallation of the package, my Wacom tablet now works fine again.

EDIT: After another restart, the problem reappears.

---

### Post by treeert on 2023-11-12
It seems to be an open issue/bug: [https://github.com/xournalpp/xournalpp/issues/5249](https://github.com/xournalpp/xournalpp/issues/5249)

I switched to Wayland now and the tablet works fine with that. Here is a quick How-To: [https://beebom.com/how-switch-between-wayland-xorg-ubuntu/](https://beebom.com/how-switch-between-wayland-xorg-ubuntu/)
In my case, there was no way to switch to Wayland on the Login screen, so I had to enable Wayland this way: [https://askubuntu.com/questions/1402671/ubuntu-no-gear-for-wayland-x11](https://askubuntu.com/questions/1402671/ubuntu-no-gear-for-wayland-x11)

Hopefully, this helps.

---

### Post by heimerdinger123 on 2023-11-12
Good evening treeert,
thank you so much for the tipp! I almost had given up hope. This is a quite simple but efficient solution you found there. Now it seems to me, like wayland is the version for creatives. :D

---

