---
title: "Installing Ubuntu Studio with repositories"
date: 2007-10-15
forum: General Help
---

### Post by Tarantella on 2007-10-15
Hello everyone (sorry, my inglish sucks). Im about to install Ubuntu Studio in my Ubuntu fesity 7.04. I have chosen de "repositories install option" and I already have done this:

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Packages in our repo:

    * ardour - Digital audio workstation (graphical gtk2 interface) (This is Ardour 2)
    * ardour-i686 - Digital audio workstation (graphical gtk2 interface) [i686] (This is Ardour 2)
    * ubuntustudio-desktop - Makes up our base desktop install.
    * ubuntustudio-audio - Ubuntu Studio audio package
    * ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
    * ubuntustudio-graphics - Ubuntu Studio graphics package
    * ubuntustudio-video - Ubuntu Studio video package
    * ubuntustudio-artwork - UbuntuStudio themes and artwork
    * ubuntustudio-gdm-theme - Ubuntu Studio GDM theme
    * ubuntustudio-icon-theme - UbuntuStudio Icon theme
    * ubuntustudio-look - Ubuntustudio look (metapackage)
    * ubuntustudio-session-splashes - Ubuntu Studio Session splashes
    * ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
    * ubuntustudio-screensaver - Ubuntu Studio's floating logo screensaver
    * ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
    * ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
    * usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
    * wired - Audio creation free software for Linux

Then i go to synaptic and i type "ubuntu studio". I have read one guide, and they say that i have to mark this packages: ubuntustudio-audio, ubuntustudio-video and ubuntustudio-graphics. But when i mark ubuntustudio graphics to install it, this message pops up:

ubuntustudio-graphics:
 Depends: gimp-svg but not to be installed

Then i tried typing in synaptic "gimp-svg" and mark that package to install, but another message pop up shows:

gimp-svg:
  Depends: gimp (=2.2.13-1ubuntu4) but to be installed 2.2.13-1ubuntu4.3

And that was all, what can i do please?

Later.

---

### Post by Tarantella on 2007-10-16
¿Is there anybody out there?  :(

---

### Post by omegamormegil on 2007-10-16
I've never tried to install Ubuntu Studio in Feisty, but Gutsy comes out in two days, and Ubuntu Studio is going to be in the Gutsy Universe repository.  So, if you plan to upgrade this Thursday anyway, it will be VERY easy to install Ubuntu Studio after you have Gutsy!  After upgrading to Gutsy, make sure you have the Universe Repository enabled, and you can just open a terminal and type (or paste):

sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-video ubuntustudio-graphics

I know this doesn't exactly answer your question, but I thought it might help!  Good luck!

---

### Post by por100pre1 on 2007-10-16
This will install everything:

```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

If aptitude complaints about: "ubuntustudio-graphics: Depends: gimp-svg but not to be installed" try ignoring that issue. :-k

Are you using repositories other than the regular ones?

---

### Post by Tarantella on 2007-10-17
Yeah, i think i messed up with some repos that i used one day i wanted to install compiz fusion (they didnt work though). I just eliminated them in synaptic, then i executed the terminal and now the package works!

Thank you both so much :D

---

