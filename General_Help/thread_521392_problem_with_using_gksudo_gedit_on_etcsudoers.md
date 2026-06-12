---
title: "problem with using gksudo gedit on /etc/sudoers"
date: 2007-08-09
forum: General Help
---

### Post by erfahren on 2007-08-09
When posting this I was given a number of links about this issue with using gksudo gedit

the error message (I realize the first has to do with the gtk2 theme I'm using [here](http://www.gnome-look.org/content/show.php?content=48553), tried fixing it as much as I could):
(gksudo:13697): Gtk-WARNING **: Theme directory 96x96/action of theme Human_Ultra_Black has no size field

(gedit:13698): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Anyway, I was trying to edit /etc/sudoers as per the instructions on the ubuntu guide wiki for [having Firestarter start without root password](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_have_Firestarter_start_without_the_root_password) but was unable to save it. I guess it opened as read-only.

The instuctions in the wiki have changed. I happened to have the instructions saved in a text file and they used to be:
export EDITOR=gedit
sudo visudo

which opened gedit to edit it, and worked. 

Is it that bug with gksudo gedit that prevents it from working. Should the wiki be changed back to what is was before?

Other posts about the gksudo gedit problem:
[http://ubuntuforums.org/showthread.php?t=195937](http://ubuntuforums.org/showthread.php?t=195937)
[http://ubuntuforums.org/showthread.php?t=366671](http://ubuntuforums.org/showthread.php?t=366671)
[http://ubuntuforums.org/showthread.php?t=353954](http://ubuntuforums.org/showthread.php?t=353954)

---

### Post by apetresc on 2007-08-09
The visudo method is definitely the correct method. Using visudo adds in a few basic security checks (like preventing multiple simultaneous edits or malformed files). sudoers is a very important file on the system, and merits these extra cautions. I'm not sure who recommended the gksudo thing, but probably someone who didn't understand what visudo was and figured just editing it as a regular file was simpler to understand. Someone should probably edit that back.

For more info on visudo, [http://www.gratisoft.us/sudo/man/visudo.html](http://www.gratisoft.us/sudo/man/visudo.html)

---

### Post by erfahren on 2007-08-09
thanks, I'll go to the UbuntuGuide.org Forum and ask about it being changed.

---

### Post by perspectoff on 2007-08-09
My understanding is that the problem is in using the gksudo instead of sudo in the first place. (Different configuration files are used.)

The Firestarter website recommended the method I put there, but I have changed it back to include both methods.

Sorry.

---

