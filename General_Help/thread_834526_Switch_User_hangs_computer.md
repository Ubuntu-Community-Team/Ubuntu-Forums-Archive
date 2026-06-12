---
title: "Switch User hangs computer"
date: 2008-06-19
forum: General Help
---

### Post by pwhitted on 2008-06-19
I am running an HP Pavilion zd7010 laptop, with the current build of Hardy installed. Choosing Switch User often - but not always - causes the computer to hang. Sometimes the screen goes black and then doesn't come back, sometimes it goes white and doesn't come back. Rarely, it actually brings me back to the login screen. This happens while using the computer and wanting to switch from one user account to another, and when trying to bring the computer back from sleep mode.

---

### Post by greyfox1 on 2008-06-20
I'm actually looking for information on this same problem.  From what I understand it is a bug related to (maybe caused by?) Compiz.  You likely won't have the problem if you turn off desktop effects, which I know isn't really much of a solution.

Honestly since desktop effects are enabled by default I cannot believe that this bug hasn't been squashed.  It is EXTREMELY annoying since it basically makes multiple user accounts unusable.  I haven't found out any solutions/workarounds yet but I hope to.

---

### Post by enchance on 2008-07-21
Same problem here. This sometimes happens to me.

---

### Post by hongleong on 2008-07-22
When I switch user on Gnome and then subsequently logout from it to go back to the original user's desktop, I'll get the white screen, which appears to be related to the gnome-screensaver.

My solution:

[LIST=1]
[*]Press CTRL-ALT-F1 to switch to virtual console.
[*]Login with the same user account as the session with "white screen".
[*]Run command: pkill -9 gnome-screensaver
[*]Press CTRL-ALT-F7 to switch back to original session... the "white screen" should be gone.
[/LIST]
Others have found that by blindly entering their passwords at the white screen, they are able to get back the original desktop too.

To prevent the white screen from appearing altogether, some have suggested to turn off screen-locking for user switching. To do that, right-click on the "User Switcher" applet, go to "Preferences" and uncheck the box for "Lock the screen after switching users".

My system specs:
* Ubuntu 8.04.1 Gnome with Compiz Fusion enabled
* Installed NVIDIA packages:
  - nvidia-glx-new 169.12+2.6.24.13-19.45
  - nvidia-kernel-common 20051028+1ubuntu8

:mrgreen:

---

