---
title: "Nautilus features in 12.10"
date: 2012-10-20
forum: General Help
---

### Post by Jimstehrman on 2012-10-20
I've been trying out 12.10, and noticed that Nautilus has changed quite a bit from 12.04...not to my liking. Namely it seems to have dropped it's menu bar, along with dual pane capabilities.
Is there any way to regain these capabilities in 12.10? Or is it possible to get the "old" version of nautilus back?

thanks!

---

### Post by howefield on 2012-10-20
Pressing F3 to get dual panes works for me. Unless I misunderstand you.

---

### Post by sgage on 2012-10-20
> **Jimstehrman said:**
> I've been trying out 12.10, and noticed that Nautilus has changed quite a bit from 12.04...not to my liking. Namely it seems to have dropped it's menu bar, along with dual pane capabilities.
Is there any way to regain these capabilities in 12.10? Or is it possible to get the "old" version of nautilus back?

thanks!

Did you apply any updates from ppa's? The nautilus that comes with stock Ubuntu is the older 3.4 version, same is in 12.04 (if you look at the package version number, it is something screwy like '3.5.90.really.3.4.2'. The official current Gnome Project version is 3.6, with the issues you mention... if you added  ppa:gnome3-team/gnome3 to your repos, it would have brought in the 3.6 version in an update.

---

### Post by Jimstehrman on 2012-10-20
on my first tries, F3 does not bring in dual pane in my case.
I also seem to have lost functionality in all of my python extensions for nautilus.
I've also heard that maybe dual pane has been dropped...?
[http://ubuntuforums.org/showthread.php?t=2013651](http://ubuntuforums.org/showthread.php?t=2013651)

---

### Post by Jimstehrman on 2012-10-20
yea, I added that ppa. I'm using gnome 3, and when I first tried it out after installing 12.10 it just wouldn't load the desktop. So I assumed I needed to install it.

---

### Post by sgage on 2012-10-20
> **Jimstehrman said:**
> on my first tries, F3 does not bring in dual pane in my case.
I also seem to have lost functionality in all of my python extensions for nautilus.
I've also heard that maybe dual pane has been dropped...?
[http://ubuntuforums.org/showthread.php?t=2013651](http://ubuntuforums.org/showthread.php?t=2013651)

Yes, dual pane has been dropped in 3.6.  Quantal comes with 3.4 - look under Help/About to get the version number (or type nautilus --version in a terminal). What do you see?

---

### Post by Jimstehrman on 2012-10-20
yup, it's 3.6.0

---

### Post by sgage on 2012-10-20
> **Jimstehrman said:**
> yup, it's 3.6.0

You shouldn't need anything from that ppa. If you ppa-purge it, you'll get the 3.4 version of nautilus with the features you (and I and many others) prefer.

You'll probably have to install ppa-purge:

sudo apt-get install ppa-purge

Then:

sudo ppa-purge ppa:gnome3-team/gnome3

and you'll be good to go. If you want to stay updated with everything besides nautilus from that ppa, you can "pin" the nautilus files so they won't be updated. I use synaptic which has an easy "lock" menu item - not sure offhand of the apt-get syntax.

---

### Post by Jimstehrman on 2012-10-20
Great!
I ended up having to re-add the repository to be able to remove it, since it couldn't find the package lists. Otherwise things are up and running again it seems.
Do you happen to know what other things are influenced by the gnome3 ppa?

---

### Post by sgage on 2012-10-20
> **Jimstehrman said:**
> Great!
I ended up having to re-add the repository to be able to remove it, since it couldn't find the package lists. Otherwise things are up and running again it seems.
Do you happen to know what other things are influenced by the gnome3 ppa?

The gnome3 ppa provides the final 3.6 versions of many Gnome programs that are held at 3.4 in the official Ubuntu release for whatever reason. Along with nautilus, there are 3.6 versions of aisleriot, brasero, soundjuicer, totem, tracker, transmission, and zenity, plus various and sundry support libraries and plugins and such.

The ricotz/testing ppa has some more, like a newer rythmbox, but is mostly geared towards Gnome Shell stuff.

---

