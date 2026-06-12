---
title: "Is KDE loaded, when I am running E17?"
date: 2006-11-01
forum: General Help
---

### Post by Gamebeavis on 2006-11-01
I loaded E17 ontop of Kubuntu (edgy). Now, when I boot to E17 (using the KDE login manager), and check my Proccess table by either using "top" or ksysguard, I find ALOT of memory being used up by KDE processes. Things like - klauncher, kinit, etc etc. Now, why are those running in E17? I know various K libraries have to be loaded in order to run programs based on K, but do these other KDE applications really need to be running, and sucking up so much RAM? If not, how do I turn them off (also, which ones)?

---

### Post by bettlebrox on 2006-11-01
Look to see if you have an .Xsession file. It can be used to start programmes when your Window Manager starts.

---

### Post by Gamebeavis on 2006-11-01
Ok, I looked in my home directory, and found a .xsession-errors file, but no .xsession. I looked in /etc/X11 and found an xsession script file. So, what does that mean??

---

### Post by bettlebrox on 2006-11-01
I just installed e17 in my Debian desktop (no room left on my Ubuntu laptop) and I noticed at the login screen I have Enlightenment sessions I can use. The first is named e-gnome and the second is named e-kde, which starts either gnome or kde using E as the window manager. Maybe your doing something similar? Where did you install E17 from?

---

### Post by Gamebeavis on 2006-11-02
I used the lost-souls repository. When KDEs login manager loads up, I get the options of signing into KDE, Enlightenment, Defualt (which is KDE). Is it possible that the KDE login manager, is loading all these things by default?? Do you think the problem would go away if I used "Entrance" for my login manager?

---

### Post by bettlebrox on 2006-11-02
Look in ~/.e/e/applications/startup to see if there are any apps listed to startup.

---

