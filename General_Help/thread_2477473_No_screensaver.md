---
title: "No screensaver"
date: 2022-07-26
forum: General Help
---

### Post by triplemaya on 2022-07-26
Once again to my great frustration screensaver is not working. I presume something is keeping the screen awake but there have been zero changes to the system. I am hoping for help tracking down the problem.
I have rebooted the pc just to make sure.
I have set screensaver to one minute.
I have set power off screen to one minute.
Screen stays on.
I have a large screen, so it is very important to me that it turns off to conserve electricity whenever the system is idle.
Have not been able to find a similar post here.

---

### Post by Dennis N on 2022-07-26
Please supply some details. What desktop environment are you using? Gnome? XFCE? It makes a difference. And then, you may use xscreensaver or something else.

---

### Post by triplemaya on 2022-07-26
Hi. Sorry. Ubuntu Mate 20.4.4 
It is on a laptop connected to a Dell screen through a Startech kvm but the problem is there when I disconnect it and just have as the laptop bare. So nothing to do with peripherals.

---

### Post by triplemaya on 2022-07-27
After some digging about I found this command:
mate-screensaver-command -a
which makes the screen saver come on. And it stays on, meaning that the problem is not some process making it quit and thus keeping the screen active. So the question is why does not not start up as it should when the system is idle.

---

### Post by Dennis N on 2022-07-27
I have the same system installed (Ubuntu MATE 20.04.4). Did you remember to check the box to activate it? (see screenshot) Just selecting a time with the slider is not enough,

Did you upgrade to mate-desktop 1.26? I know there is a PPA to do that. If so, know that the screensaver won't work with Wayland. You must use Xorg.

---

### Post by triplemaya on 2022-12-21
Thanks Dennis N. That may well have been the problem. Problem went away a while back but probably because I looked at the settings and used the tick this time!

---

