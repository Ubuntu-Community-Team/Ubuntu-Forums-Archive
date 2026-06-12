---
title: "Touchpad Problems driving me insane..."
date: 2007-12-11
forum: General Help
---

### Post by Junk_head on 2007-12-11
Hello ubuntu community!
Ive been havin issues with my laptop's touchpad and point stick, ive used qsynaptics/touchpad app, and turned off tap to clicking thinking that this might have been causing a conflict between the two sets of L/R clickers (one set for the pad and one set for the point stick) The mouse would move around the screen but it would be non responding to any clicks. Ive usaully just alt+ctrl+del to restart, and it solves it but it lasts maybe 5 to 10 mins before the mouse ignores the clicks again. The event usaully happens within firefox, while going through tabs and such, but it affects the whole thing, i'll be at my desktop and wont be able to do anything except restart.
My laptop's a Toshiba Tecra A8 and im running ubuntu 7.10

---

### Post by Junk_head on 2007-12-12
Bump

---

### Post by Harpoon on 2007-12-12
I am not familiar with the extra hardware you are using, but if it can be used to replace the touchpad there is a solution.

sudo synclient touchpadoff=1

will disable the touchpad and click buttons.

sudo synclient touchpadoff=0

will turn it back on.

Hope that helps.

---

### Post by Junk_head on 2007-12-12
Unfortunately this also turns off both sets of buttons.
The point stick is like those little red nipple on ibm/levano laptops, on the keyboards.

---

### Post by Junk_head on 2007-12-14
Bump, sorry if this thing's been here for so long, but this issue is just so frustrating.

---

