---
title: "Re: testing unity-session in 17.10/nautilus ppa"
date: 2017-11-03
forum: General Help
---

### Post by monkeybrain20122 on 2017-11-03
Not sure if I should report it here (or anything to be report?)

 It is 17.04 but I am pretty sure this is true for 18.04 (I will make a test install of 18.04 when the daily iso comes out. I am still in the process of discovering bugs in 17.04) The package indicator-application needed for unity is in conflict with gnome shell. e.g skype doesn't show up in gnome shell's panel if this is installed, click close it just disappears and run in the background. But if remove it skype no longer shows up in Unity's panel so it has to be installed. [https://askubuntu.com/questions/966987/indicator-icons-do-not-appear-after-upgrade-to-ubuntu-17-10](https://askubuntu.com/questions/966987/indicator-icons-do-not-appear-after-upgrade-to-ubuntu-17-10)

Strictly speaking though the conflict may not be with gnome shell per se (but some of Ubuntu's modification) since the great idea of gnome's devs is to remove the icon tray and let applications like skype run in the background so users have no way to know they are running unless someone calls  (:o) . it is (yet another anti-user) feature of genome but not a bug [http://www.omgubuntu.co.uk/2017/09/will-you-miss-gnome-legacy-tray](http://www.omgubuntu.co.uk/2017/09/will-you-miss-gnome-legacy-tray).

---

### Post by QIII on 2017-11-03
Moved to General Help.

Since your issue is with 17.04, the Ubuntu Development Version sub-forum is not appropriate.

Cheers!

---

### Post by monkeybrain20122 on 2017-11-03
This only happens in ubuntu-xorg (gnome-xorg, that is) In wayland session skype shows up in panel even if indicator-application is installed.

---

### Post by ajgreeny on 2017-11-03
Are you really talking of 17.04 or 17.10; I am a bit confused as it seems more likely 17.10 from what you are saying?

---

### Post by monkeybrain20122 on 2017-11-03
Oops I meant 17.10

---

