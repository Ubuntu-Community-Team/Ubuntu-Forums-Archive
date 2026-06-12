---
title: "Latest version of Midnight Commander?"
date: 2013-12-06
forum: General Help
---

### Post by LeeU on 2013-12-06
I was wondering if anyone knew where I can get a 'deb' version of the latest version (4.8.11) of Midnight Commander? I am using Ubuntu 12.04 and, even after adding the repository info listed on [their website]("http://www.midnight-commander.org/wiki/Binaries/"), my Package Manager only shows the 3.4.8.11-1 version. I can download the source code and do an install but I would prefer using the 'deb' file, if possible. I currently use Gnome Commander but it hasn't been updated since December 2011, and needs some improvement (although it works pretty good as it is). I wanted to try out Midnight Commander and see how it works (I don't like Nautilus) but much of the improvements are in the newer version.

Anyway, I was just hoping to not have to do an install, if possible.

---

### Post by Bucky Ball on 2013-12-06
*Thread moved to **General Help**.*

---

### Post by LeeU on 2013-12-06
How is a file manager considered "gaming and leisure", especially when there is already another post in the general forum: [HowTo make Midnight Commander remember the working directory ]("http://ubuntuforums.org/showthread.php?t=2097464&highlight=midnight+commander")?

---

### Post by Bucky Ball on 2013-12-06
You are wanting a .deb package of a game, aren't you? This is the best place to ask for one.

---

### Post by LeeU on 2013-12-06
No, "Midnight Commander" is a **file manager** (e.g., as in Nautilus), not a game.

---

### Post by Dave_L on 2013-12-06
It sounds like your package manager *does* have the latest version.  Does the package manager indicate the version as "3.4.8.11-1" or "3:4.8.11-1" ?  Note that the "3:" at the beginning is not part of the "internal" version number.

Within mc, you can use F1 (or click on the "Help" button at the bottom) to view the version number.

And I can confirm that Midnight Commander is a console file manager, not a game. ;)

---

### Post by Bucky Ball on 2013-12-06
Strange. I have 3:4.8.1-2. In the repos. Using 12.04. 

[QUOTE=Dave_L]And I can confirm that Midnight Commander is a console file manager, not a game. [/QUOTE]

Downloaded fine and just having a play with it now. Learn something everyday. ;)

---

### Post by Dave_L on 2013-12-06
> **Bucky Ball said:**
> Strange. I have 3:4.8.1-2. In the repos. Using 12.04. 

Downloaded fine and just having a play with it now. Learn something everyday. ;)

I'm also running 12.04, and have the same version of mc as you.  I think LeeU is getting the newer verison from  a PPA.

---

### Post by oldos2er on 2013-12-06
It just updated on trusty this morning: [http://packages.ubuntu.com/trusty/mc](http://packages.ubuntu.com/trusty/mc)

---

### Post by LeeU on 2013-12-06
Ah, I wondered why the colon was there. Yes, I have version 3:4.8.11-1. Thanks Dave for clearing that up.

BTW, checking the version in help give the Gnome Terminal version number (e.g., 3.4.1.1), not the version of MC.

---

### Post by Dave_L on 2013-12-07
> **LeeU said:**
> Ah, I wondered why the colon was there. Yes, I have version 3:4.8.11-1. Thanks Dave for clearing that up.

BTW, checking the version in help give the Gnome Terminal version number (e.g., 3.4.1.1), not the version of MC.

Gnome intercepts the F1 key and gives you its help page. The MC help page can be accessed by clicking on the MC Help button with the left mouse button. Or you can open a (non-GUI) shell session with Ctrl+Alt+F2 and run MC; then F1 will activate the MC help page. (In case you're not familiar with Ctrl+Alt+F2, note that Ctrl+Alt+F7 returns you to the normal GUI session.)

---

