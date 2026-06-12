---
title: "How do I get the 3D cube in Desktop Effects?"
date: 2007-08-02
forum: General Help
---

### Post by mjpatey on 2007-08-02
I just re-installed the "standard" compiz after failing to get compiz-fusion working using a tutorial.  I had to uninstall lots of things, then re-install compiz.  Under Dektop Effects, "Rotating Cube" is checked.

I do have wobbly windows, but I can't figure out how to make the cube work.  I tried Ctrl-Alt-cursor keys, Ctrl-Alt-drag the mouse... no worky.

Any idea how to rotate the cube?  I've searched Synaptic for Gnome Compiz Config (and other similar search terms) to try and install the configuration tool mentioned in other posts, but I can't seem to find such a configurator.  Any idea?

I'm running Feisty with an nVidia 6200 card on a 2.3GHz Pentium IV with 1.5GB RAM, and have successfully run complex Beryl effects in the past with no trouble.

Thanks!

-Mark

---

### Post by Happy_Man on 2007-08-02
The package is gnome-compiz-manager.

You have to hold down ctrl+alt+left mouse button, and then drag.

---

### Post by yorkie on 2007-08-02
COMPIZ CUBE  If you want to get the cube to work do the following commands

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

then its ctrl,alt and left or right arrow key

---

### Post by mjpatey on 2007-08-02
Yay, Yorkie!  Thanks, it works perfectly!  Little doggies have yet to fail me.  :-)

Happy_Man, I installed the package; thanks for the info!  I don't know how to run it, though.  Simply typing gnome-compiz-manager doesn't do it.  Also, nothing appears under System Tools for it.  Where does it live?

Thanks again!

-Mark

---

### Post by mjpatey on 2007-08-02
I think I found my answer to the config program question... it's under System -> Preferences -> GL Desktop.  :-)

---

### Post by weblordpepe on 2007-08-02
If you want to go all super-awesome, you'll want to try compiz-fusion. It has all sorts of neat things, like fishies swimming around inside the cube.

---

### Post by mjpatey on 2007-08-02
Yeah, that's what got me in trouble in the first place!

Maybe next time I'm feeling dangerous.  :-)

-Mark

---

### Post by weblordpepe on 2007-08-02
If you install compiz-fusion, and then use the GLdesktop program it will break the compiz stuff.
Ya gotta use this repository
> # Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

### Post by Happy_Man on 2007-08-03
> **weblordpepe said:**
> If you install compiz-fusion, and then use the GLdesktop program it will break the compiz stuff.
Ya gotta use this repository
Yeah, but first run ```
sudo apt-get remove compiz-core desktop-effects
``` before adding the repos and upgrading.

---

