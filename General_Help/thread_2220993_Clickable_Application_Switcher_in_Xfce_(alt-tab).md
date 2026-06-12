---
title: "Clickable Application Switcher in Xfce (alt-tab)"
date: 2014-04-30
forum: General Help
---

### Post by Sunbriel on 2014-04-30
I've already googled all the possible ways of doing this, but none has really worked, that's why I'm now asking here for help.

I decided to bind Alt-tab/native Xubuntu/Xfce application switcher to one of my mouse buttons (Logitech G400S). I managed to do so with help of xbindkeys, but it doesn't work as I'd like it to. When I click the mouse button, application switcher opens, but the application icons are not clickable, thus I cannot really switch between apps like I usually would under Windows. Is there a working script that would allow me to open Application switcher and then click on the app icon, or an alternative switcher that is not part of Compiz nor SuperSwitch and Skippy-XD?

---

### Post by bapoumba on 2014-05-01
What does happen if you scroll over the task bar windows list ?

---

### Post by Sunbriel on 2014-05-01
When you click on that mousr button, Alt-tab switcher appears and you can click with mouse in application icons. That'sthe action I want to reproduce in Xubuntu.

---

### Post by brainwash on 2014-05-01
This feature was implemented some time ago and merged upstream recently (sadly too late for Xubuntu 14.04). However, you can compile and install xfwm4 from source [1] or simply use my daily PPA [2].

[1] [http://git.xfce.org/xfce/xfwm4/](http://git.xfce.org/xfce/xfwm4/)
[2] [https://launchpad.net/~thad-fisch/+archive/xfce-git](https://launchpad.net/~thad-fisch/+archive/xfce-git)

---

### Post by Sunbriel on 2014-05-04
> **brainwash said:**
> This feature was implemented some time ago and merged upstream recently (sadly too late for Xubuntu 14.04). However, you can compile and install xfwm4 from source [1] or simply use my daily PPA [2].

[1] [http://git.xfce.org/xfce/xfwm4/](http://git.xfce.org/xfce/xfwm4/)
[2] [https://launchpad.net/~thad-fisch/+archive/xfce-git](https://launchpad.net/~thad-fisch/+archive/xfce-git)

Thank you very much! Now the "only" thing I have to figure out is how to call Alt-Tab window with a mouse button and make it stay open so I can click on a desired app's icon. "xdotool keydown alt key Tab; sleep 2; xdotool keyup alt" and other variants of this aren't working properly. When I click on the assigned mouse button it only switches between first two open apps on the list. Any idea how to make it work?

Edit:

Nevermind. "xdotool keydown alt key Tab; sleep 2; xdotool keyup alt" actually works. A reboot/logout was needed for xbindkeys to start working properly.

---

