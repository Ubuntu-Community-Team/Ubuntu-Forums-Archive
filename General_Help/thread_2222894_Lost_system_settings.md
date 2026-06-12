---
title: "Lost system settings"
date: 2014-05-08
forum: General Help
---

### Post by youngie on 2014-05-08
Hi, I wonder if someone could please help. I seem to have lost most of my system settings:
[ATTACH=CONFIG]252993[/ATTACH]

I'm not sure when this happened, I have had problems with my soundcard and also getting MTP working with my phone so it could have been when I was messing about with these. I've tried "sudo apt-get install --reinstall gnome-control-center" no joy. Any help please, thanks.

---

### Post by grahammechanical on 2014-05-08
What version of Ubuntu are you using? If it is 14.04 then I am certain that Ubuntu no longer uses gnome-control-center. It has been replaced by unity-control-center. The Synaptic Package Manager says this about unity-control-center:

> This package contains configuration applets for the GNOME desktop, allowing to set accessibility configuration, desktop fonts, keyboard and mouse properties, sound setup, desktop theme and background, user interface properties, screen resolution, and other GNOME parameters.


It also contains a front end to these applets, which can also be accessed with the GNOME panel or the Nautilus file manager. 


Regards.

---

### Post by youngie on 2014-05-09
Yeah I am using 14.04, thanks I'll try --reinstall unity-control-center.

---

### Post by youngie on 2014-05-12
Thank you reinstalling unity-control-centre fixed it.

---

