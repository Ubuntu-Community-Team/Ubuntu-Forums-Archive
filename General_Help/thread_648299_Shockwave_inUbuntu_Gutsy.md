---
title: "Shockwave inUbuntu Gutsy?"
date: 2007-12-23
forum: General Help
---

### Post by Dojan5 on 2007-12-23
Im new to Ubuntu and just lurnt how to use Add/Remove programs thingy...
But i can't find Shockwave player there...
Where and how do i install that?
The Terminal?
Thanks in whatever it was called again....
/
Joel

---

### Post by bwhite82 on 2007-12-23
Unfortunately shockwave isn't available for Linux. You can, however, install the Windows version of firefox in wine and the windows version of shockwave on top of that in wine.

---

### Post by Dojan5 on 2007-12-23
> **Soldierboy said:**
> Unfortunately shockwave isn't available for Linux. You can, however, install the Windows version of firefox in wine and the windows version of shockwave on top of that in wine.

Okay...
Thanks, but, how exactly do i do that?
Please explain...
Thanks

---

### Post by Salpiche on 2007-12-23
> Edit:
As stated above and below not Shockwave but Flash...


open a terminal and do a > sudo gedit /etc/apt/sources.list
it will open a text file then look for > #deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
then remove the # from the front, save and close
on the terminal type > sudo apt-get update

then open your add remove  and you should be able to find it

Note:
make sure that you only remove the # from the lines that start with deb-...


Hope this help

Jose

---

### Post by bwhite82 on 2007-12-23
I must reiterate, shockwave is not available for Linux, flash is (contrary to popular belief they are not the same.) If you truly need shockwave (for the web? or stand-alone version?) you will need to install wine.

-Make sure you have all of your repositories enabled

-Search for wine in synaptic

-install it

-Download FF windows executable from their website to your desktop

-Do the same for Shockwave player

-Right click on the FF executable and click "Install with wine"

-Do the same for shockwave executable

-Open your windows-version of FF via the wine menu in 'applications'

-surf to the website where you want to view the shockwave-embedded media, and you should be in business.

*This is assuming that you are trying to view a website with shockwave content, you may want the stand-alone player if you downloaded a shockwave movie.

---

