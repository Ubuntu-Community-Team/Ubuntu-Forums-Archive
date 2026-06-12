---
title: "uninstaling KDE does not work"
date: 2008-02-16
forum: General Help
---

### Post by fargus on 2008-02-16
I recently decided to give KDE and Xfce a try. (I recently switched to linux after I bought a laptop in October and had a lot of problems with Vista, and I use Ubuntu 7.10) To install, I used the commands

sudo aptitude install kubuntu-desktop

and

sudo aptitude install xubuntu desktop

I would really like to get rid of both of these off of my computer, as they are taking up a lot of hard drive space and filling my gnome menus with programs I will never use. I tried to uninstall using the commands

sudo aptitude remove kubuntu-desktop

and

sudo aptitude remove xubuntu-desktop

after doing this, all of the applications for KDE and Xfce are still there, and I can restart X and go into a KDE or Xfce session with no noticeable problems. Is there a way to get rid of these programs? Also, how do I get rid of enlightenment, as I no longer want that (or E-gnome, or E-KDE) as a session option.

---

### Post by fargus on 2008-02-16
Something to note: I also installed KDE4 and that is an option under sessions in GDM. I would like to get rid of it too. I added the source 

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

and I used the command

sudo apt-get install kde4-core

---

