---
title: "Ubuntu or Kubuntu?"
date: 2006-10-13
forum: General Help
---

### Post by smitty88 on 2006-10-13
Calling me be a beginner would probably be generous. A friend installed Fedora 3 for me year or two ago and I like it, but rather than upgrade he suggested Ubuntu. 
   My needs are fairly simple in my home system - In addition to Firefox/T-Bird I use GnuCash via Comcast cable, Open Office, and have to be sure I'm able to use K-Organizer as it has a lot of irreplaceable long-term info.
   1. With these simple needs, does it make any difference whether I use Ubuntu or Kubuntu?
   2. I'd like to pay someone who really knows this stuff to spend a few hours here in Berkeley to help with installing, help with some questions I have, and maybe get me a bit more up to speed. I'd like someone who really knows this stuff as pvs installer had problems with existing XP and partitioning and may have done some things in non-standard ways. How can I fund such a person?

---

### Post by Topsiho on 2006-10-13
Kubuntu has the KDE desktop, Ubuntu the Gnome desktop
KOrganizer is a KDE program so you need the KDE desktop to run it.

The choice seems clear.

However: if you have both desktops installed then you can run both KDE and Gnome programs as in that case you'll have all the necessary libraries installed.

So: Install Ubuntu, as in the USA Gnome is the preferred desktop (I suppose) and after that install the kubuntu desktop also.

I am not quite sure about the precise command to do this as it is a while ago I did this myself, but if I am mistaken someone will correct me, or you'll look it up somewhere else:

Do in a terminal:

sudo apt-get install kubuntu-desktop

and give your password.

Sit back a while (and answer yes if asked for) and you have both worlds on your system :)

Topsiho

---

### Post by aysiu on 2006-10-13
These are the differences I've seen:
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

I would advise, if you are going to install Kubuntu, that you *aptitude* instead of *apt-get*. Full instructions here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Full reasoning here:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

