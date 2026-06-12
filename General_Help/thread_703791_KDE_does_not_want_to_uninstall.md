---
title: "KDE does not want to uninstall"
date: 2008-02-21
forum: General Help
---

### Post by fargus on 2008-02-21
I recently decided to give KDE and Xfce a try. (I recently switched to linux after I bought a laptop in October and had a lot of problems with Vista, and I use Ubuntu 7.10) To install, I used the commands

sudo aptitude install kubuntu-desktop

and

sudo aptitude install xubuntu desktop

I would really like to get rid of both of these off of my computer, as they are taking up a lot of hard drive space and filling my gnome menus with programs I will never use. I tried to uninstall using the commands

sudo aptitude remove kubuntu-desktop

and

sudo aptitude remove xubuntu-desktop

after doing this, all of the applications for KDE and Xfce are still there, and I can restart X and go into a KDE or Xfce session with no noticeable problems. Is there a way to get rid of these programs? Also, how do I get rid of enlightenment, as I no longer want that (or E-gnome, or E-KDE) as a session option. Something to note: I also installed KDE4 and that is an option under sessions in GDM. I would like to get rid of it too. I added the source

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

and I used the command

sudo apt-get install kde4-core

---

### Post by PeterJS on 2008-02-21
The packages you installed and unsinstalled were the KDE and XFCE meta-packages, the way they work is they specifiy a bunch of packages as dependancies, and by installing them you get all the sub packages under one easy to remember name, the problem as you just found out, comes when uninstalling them, removing the meta package, just removes it, and not any of the actual packages it comprises.

See this guide on getting back to a pure gnome desktop:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by puzzledinmn on 2008-02-27
Thanks to PeterJS.  I had experimented with the KDE Desktop and decided I just wanted GNOME.  I searched the forums and only found an old answer that did not work.  This uninstalled the KDE Desktop and meta-packages.  The only complication was that I wanted VLC and Amorak but it is easier just to reinstall than edit the uninstall list.

---

### Post by CoolDreamZ on 2008-02-29
**[COLOR="Red"]Be warned[/COLOR]** - this also removes Apache and MySQL. This is annoying to say the least. Are these part of KDE?? I managed to re-install them OK without loss of data but I did not expect these to be removed. I obviously didn't check the list of packages well enough. :roll:

The good news is that the KDE stuff has gone and I now have approx 1Gb of extra disk space available.

---

