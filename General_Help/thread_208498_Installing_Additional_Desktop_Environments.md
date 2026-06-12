---
title: "Installing Additional Desktop Environments"
date: 2006-07-03
forum: General Help
---

### Post by ahaslam on 2006-07-03
While testing a beta of Dapper a while back I installed kubuntu-desktop & xubuntu-desktop. It all worked in harmony to begin with, apart from cluttered menus  containing KDE & GNOME apps.
After a couple of days my GNOME session became a little unresponsive (thing took a few extra secs to load) and my theme colours all turned brown. My Xfce session was seriously affected, none of the menus were accessible! Only the KDE session worked normally (though it did seem a little sluggish).

I want to know if all that is normal, or if it's probably due to its beta status? I ask because I'm thinking of doing it again, but don't want to screw up my installation. The only hassle that I'm willing to subject myself to is editing the menus.

I've just looked in Synaptic and to install xubuntu-desktop, it says that abiword-gnome & libgoffice-1-2 need to be removed (they're to be replaced with abiword & libgoffice-gtk-1-2). Will this screw up Abiword in GNOME? Can't both exist?

Thank you for reading all of that, all comments & suggestions are welcome.

Tony.

---

### Post by Rui Pais on 2006-07-03
hi,
i have e17, gnome, fluxbox and xfce4 (and parts of kde since my kid likes 1 or 2 kde things). Never get any problem with that. That have different config files, so they will not collide. 
Maybe xfce/gnome themes will interact but its just a question of fiddling with preferences.

About abiword-gnome beeing replace. Thats not a problem (in fact abiword will eventually be a little faster, since its slightly lighter). If you want to keep abiword-gnome or keep gnome your main DE and reduce at minimum the risk of xfce/gnome coexist, i recommend try to apt-get only xfce4 and not xubuntu-desktop.
If something is miss do a search for xfce and install what you need (again lighter) ;)

Have fun

---

### Post by ahaslam on 2006-07-04
Thanks for your reply, I'll go for it later this week.
I'll post how I get on, maybe with a few screens.

Tony.

---

### Post by ahaslam on 2006-07-04
I have another question that I forgot to include:

When installing the additional desktops, a different boot splash (or is it upsplash?) is is also installed. I really like the look of the standard Ubuntu boot sequence and definitely want to keep it. How can I restore this once the additional DE's have been installed?

Thank you,

Tony.

---

### Post by Rui Pais on 2006-07-04
hi, no problem.

that happens if you install k/xubuntu-desktop, meta-packages that add costumize stuff specific of they desktop. 

A simple solution is just install the aditional DEs and not they meta-packages.
apt-get install xfce4 or apt-get install kde 
(i don't even used any xxx-desktop, since they add extra stuff that i don't use or want...)

if you want to go with the k/xubuntu-desktop, you can change usplash (i think its what is changed) use the last two commands of the [USplashCustomazation Wiki]("https://help.ubuntu.com/community/USplashCustomizationHowto") to set the usplash image you want and sudo gdmsetup to reput any gdm look changes.
Grub splash isn't change, i think (but anyway, you can always edit menu.lst)

:)

---

### Post by ahaslam on 2006-07-04
Thanks again mate.

I've backed up the upsplash file the guide refers to, just in case.
If I do install just the DE's and not (?)ubuntu-desktop, how do I use the DE - do I still select what session I want at login? 

Thank you,

Tony.

PS. I've just looked in Synaptic, it seems that if (?)ubuntu-desktop is to be installed, (?)ubuntu-artwork-usplash can be deselected before installation. That shoud stop the artwork from changing.

Tony.

---

### Post by aysiu on 2006-07-04
Yes, you select at session, just as you did before.

And most of the bare essential configuration packages are included, but you may find a few settings menus missing--particularly for XFCE.

---

### Post by Rui Pais on 2006-07-04
[QUOTE=Anthony Haslam]
If I do install just the DE's and not (?)ubuntu-desktop, how do I use the DE - do I still select what session I want at login? Finally, are all necessary configuration packages included with the DE?[/QUOTE]
Hi,
yes all configuration files need will be there and you will have access to them through gdm login.

edit: aysiu was quicker ;)

yes XFCE miss some items (i don't remember now which ones) but its easy to get what is missing using synaptic or aptitude search xfce

---

### Post by ahaslam on 2006-07-04
Thank you both.

So the only real difference between the two methods is whether or not extra packages are installed eg. Amarok, K3b, etc?

To summarise (please correct me if Im wrong): 
If you want a minimal install, just install the DE and add clutter as & when. If you want the full desktop, with all default apps (?)ubuntu-desktop would be the choice.

Thanks again,

Tony.

---

### Post by ign on 2006-07-05
do you think it would be safe for a starting user to install xfce? i don't like the standard DE very much and would like to give xfce a try, but i don't want to risk loosing capabilities in the gnome apps because i want to be able to use both.
what would be your advise, installing xubuntu-desktop or xfce?

---

### Post by Rui Pais on 2006-07-05
[QUOTE=ign]do you think it would be safe for a starting user to install xfce? i don't like the standard DE very much and would like to give xfce a try, but i don't want to risk loosing capabilities in the gnome apps because i want to be able to use both.
what would be your advise, installing xubuntu-desktop or xfce?[/QUOTE]
Yes, it's perfectly safe.
Xfce will not delete nothing from gnome. Will in fact add an entry for every gnome app it finds in xfce menu. 
You can use both, just choosing at gdm session options to which one you want to login :)

You can remove xfce4 later if you don't like it.

---

### Post by ign on 2006-07-05
[QUOTE=Rui Pais]Yes, it's perfectly safe.
Xfce will not delete nothing from gnome. Will in fact add an entry for every gnome app it finds in xfce menu. 
You can use both, just choosing at gdm session options to which one you want to login :)

You can remove xfce4 later if you don't like it.[/QUOTE]

thank you very much for your fast reply, i did install the xubuntu-desktop using apt-get and played a while but it wasn't what i was looking for (too gnomish) so i removed it. for anyone that wants to install to give it a try i would recomend to install using aptitude, as it will be a lot easier to remove (aptitude will automatically remove all the extra packages).
if you installed using apt-get (or synaptic) this is what i did to remove it again: [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

---

