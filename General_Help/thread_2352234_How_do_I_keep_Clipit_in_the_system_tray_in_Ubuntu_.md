---
title: "How do I keep Clipit in the system tray in Ubuntu Mate 16.04"
date: 2017-02-10
forum: General Help
---

### Post by sillyboy on 2017-02-10
Hello all,  How do I keep the app Clipit in the bar that has the speaker icon, day and  date, time, etc.  Tbird and FF icons stay there when 16.04 is rebooted.   I just installed 16.04 LTS.  I moved up from U 12.04.  The Clipit icon always remained on the bar.  Clipit did come bundled with  16.04, in Accessories.

Thank You

---

### Post by sillyboy on 2017-02-15
Anybody?

---

### Post by #&amp;thj^% on 2017-02-15
What I did was add it to **"/etc/xdg/autostart/clipit-startup.desktop".**
So mine now Looks lake this (Add to the bottom of the file):
```
Type=Application
OnlyShowIn=GNOME;XFCE;MATE;LXDE;Unity;
X-GNOME-Autostart-enabled=true
```
And if this dose not work there is always [Parcellite]("https://apps.ubuntu.com/cat/applications/precise/parcellite/") which is what Clipit is forked from.
Kind Regards

---

### Post by sillyboy on 2017-02-26
Thank You... I will try

---

