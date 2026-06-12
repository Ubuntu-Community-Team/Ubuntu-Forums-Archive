---
title: "Randomly pasting last clipboard content at mouse, makes computer unusable"
date: 2023-08-27
forum: General Help
---

### Post by faraway1nspace on 2023-08-27
A new issue just occurred that is making my ubuntu computer unusable, and I don't know if it is hardware or a bad update.
Symptom: it keeps randomly pasting the last content of my clipboard every 0.5 second to 4 seconds.    Wherever my cursor is located,it will draw focus there, and then start pasting.
Other symptoms: typing 'e' non-stop, browser tabs will randomly open,  randomly close,     sometimes I can't select a browser tab, sometimes I can't bring up the HUD-display   ( i.e., the "super" won't pop-up),but these are less common than the non-stop random pasting.
 This happens in my brower, emacs, other text-editors -- everywhere seemingly. It happens in Ubuntu  Wayland,   i3-wm, and Ubuntu Default

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:    20.04
Codename:    focal 


Even typing this message was  very very challenging.  
I've never seen these before. 
How could I even start diagnosing what is wrong?
I *think* it started after an update on Friday (Aug 26th 2023).


Here are the most recent updates that I think may have caused the issue: 


Here are the most recent updates that I think may have caused the issue: 
pgrade:  python3-distro-info:amd64 (0.23ubuntu1, 0.23ubuntu1.1),  libgpgmepp6:amd64 (1.13.1-7ubuntu2, 1.13.1-7ubuntu2.1),  python3-software-properties:amd64 (0.99.9.11, 0.99.9.12),  libwbclient0:amd64 (2:4.15.13+dfsg-0ubuntu0.20.04.3,  2:4.15.13+dfsg-0ubuntu0.20.04.4), libgpgme11:amd64 (1.13.1-7ubuntu2,  1.13.1-7ubuntu2.1), libsnmp-base:amd64 (5.8+dfsg-2ubuntu2.7,  5.8+dfsg-2ubuntu2.9), software-properties-gtk:amd64 (0.99.9.11,  0.99.9.12), samba-libs:amd64 (2:4.15.13+dfsg-0ubuntu0.20.04.3,  2:4.15.13+dfsg-0ubuntu0.20.04.4), libsnmp35:amd64 (5.8+dfsg-2ubuntu2.7,  5.8+dfsg-2ubuntu2.9), distro-info:amd64 (0.23ubuntu1, 0.23ubuntu1.1),  carla-bridge-win64:amd64 (5:2.6.0~git20230724.2, 5:2.6.0~git20230804),  ufw:amd64 (0.36-6ubuntu1, 0.36-6ubuntu1.1), libsmbclient:amd64  (2:4.15.13+dfsg-0ubuntu0.20.04.3, 2:4.15.13+dfsg-0ubuntu0.20.04.4),  carla-bridge-linux32:i386 (5:2.6.0~git20230724.2, 5:2.6.0~git20230804),  python3-protonvpn-nm-lib:amd64 (3.14.0-1, 3.16.0-1),  software-properties-common:amd64 (0.99.9.11, 0.99.9.12)
End-Date: 2023-08-23  20:07:05

Start-Date: 2023-08-26  07:08:33
Commandline: /usr/bin/unattended-upgrade
Upgrade:  gcc-9-base:amd64 (9.4.0-1ubuntu1~20.04.1, 9.4.0-1ubuntu1~20.04.2),  cpp-9:amd64 (9.4.0-1ubuntu1~20.04.1, 9.4.0-1ubuntu1~20.04.2),  libgfortran-9-dev:amd64 (9.4.0-1ubuntu1~20.04.1,  9.4.0-1ubuntu1~20.04.2), libasan5:amd64 (9.4.0-1ubuntu1~20.04.1,  9.4.0-1ubuntu1~20.04.2), libstdc++-9-dev:amd64 (9.4.0-1ubuntu1~20.04.1,  9.4.0-1ubuntu1~20.04.2), g++-9:amd64 (9.4.0-1ubuntu1~20.04.1,  9.4.0-1ubuntu1~20.04.2), gcc-9:amd64 (9.4.0-1ubuntu1~20.04.1,  9.4.0-1ubuntu1~20.04.2), gfortran-9:amd64 (9.4.0-1ubuntu1~20.04.1,  9.4.0-1ubuntu1~20.04.2), libgcc-9-dev:amd64 (9.4.0-1ubuntu1~20.04.1,  9.4.0-1ubuntu1~20.04.2)
End-Date: 2023-08-26  07:08:42

---

### Post by ajgreeny on 2023-08-27
It almost sounds as if you have a sticky keyboard problem with Ctrl+V being repeated.

Does the problem continue but with new repeated pasting if you copy something else with Ctrl+C?

---

### Post by faraway1nspace on 2023-08-27
Yes to "the problem continue but with new repeated pasting if you copy something else with Ctrl+C?" 
 but this behaviour happens in both emacs (where paste is ctrl-Y) as well a generic editors (where paste is ctrl-V)... So, I think that means it cannot literally be a sticky key issue

---

### Post by faraway1nspace on 2023-08-27
SOLVED (kinda): 
- this is what solved it for me: I went into: Setitings -> Mouse & Touchpad -> Toggle: Off touchpad. Then I plugged in an optical mouse and used it for a bit (during which the bad behaviour stopped). Then I turned back on the touchpad... behaviour disappeared for an hour so far... 
No Idea why that worked, but I guess I reset something pathological with the touchpad

---

### Post by Holger_Gehrke on 2023-08-27
And to give you the reason: middle click on pointing devices is 'paste selection' (note that this is the selection, **not** the clipboard). If your touchpad is set to produce middle click for three-finger tap (like mine is), than that would explain the problem. It misread your hand touching the touchpad while typing as a three-finger tap.

Holger

---

