---
title: "Software sources (main) cannot be enabled"
date: 2015-09-27
forum: General Help
---

### Post by Madhuvan on 2015-09-27
Hello,

I tried to install recordmydesktop, it got installed but does not show in the applications. I tried checking the software sources and all the boxes are unticked. I tried ticking them but after getting ticked it gets automatically unticked instantly. Please help.

---

### Post by QDR06VV9 on 2015-09-27
Open a terminal, What is the output of
```
[COLOR=#000000]recordmydesktop[/COLOR]
```

---

### Post by Madhuvan on 2015-09-27
Hi Runrickus thank you...

---

### Post by QDR06VV9 on 2015-09-27
Sometimes when using gnome 3 after installing things(Software) they will show up the next time you login.
Can you enable other [COLOR=#000000] software sources  yet? Or is that still an issue.
Just in case you still can not enable software sources that you need or want, there is always command line.
By way of 
```
[/COLOR]gksu gedit /etc/apt/sources.list[COLOR=#000000]
```
 This is Just a short  Example of Mine
> [/COLOR]## Uncomment the following two lines to add software from Canonical's## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
**# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner**
**# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner**
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-proposed main multiverse restricted universe[COLOR=#000000]
You will notice that any line starting with "#" means commented out or disabled so to enable simply remove the "#" in front of the line you want.
Save and Exit gedit.
Kind Regards[/COLOR]

---

### Post by Madhuvan on 2015-09-28
Hello RunRickus I tried it in gedit and it seems to work for all other software. Recordmydesktop shows as installed but doesn't show up in App Drawer neither runs.

---

### Post by Madhuvan on 2015-09-28
The GUI software sources doesn't work either.

---

### Post by QDR06VV9 on 2015-09-28
Try this for me.
```
sudo apt-get install gtk-recordmydesktop
```

I never was a big fan of the SoftWare Center, I usually just install from command line, and if I need to see anything from packages I use 
synaptic package manager. 
Been doing it that way for years, so maybe Old Habits Die hard.
Have you messed with the source's since the last time? And after trying to change them, are you ever prompted for a password?

---

### Post by Madhuvan on 2015-09-28
Thank you once again Runrickus. That worked. I find it easier this way too. No I haven't really done anything with the Software Center. I not care about it anymore. I can install software and it shows, the rest is not important. If you say so I will mark this as solved. Thank you.

---

### Post by QDR06VV9 on 2015-09-29
> **Madhuvan said:**
> Thank you once again Runrickus. That worked. I find it easier this way too. No I haven't really done anything with the Software Center. I not care about it anymore. I can install software and it shows,_ the rest is not important. If you say so I will mark this as solved. Thank you._
That would be up to you. If your happy with that.
I would be curious if synaptic has different results with changing the enabled repository's though?
Kind Regards

---

