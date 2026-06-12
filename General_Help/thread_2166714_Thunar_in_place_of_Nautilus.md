---
title: "Thunar in place of Nautilus"
date: 2013-08-10
forum: General Help
---

### Post by Uncle Spellbinder on 2013-08-10
So, is it possible to install Thunar and have it act is the default file manager in Ubuntu 13.04?

---

### Post by fdrake on 2013-08-10
you can install xfce (which uses thunar file manager) alongside gnome and use that desktop manager when you login .
[http://askubuntu.com/questions/223536/how-can-i-install-xfce-along-side-unity](http://askubuntu.com/questions/223536/how-can-i-install-xfce-along-side-unity)

i do not htink you can use thunar with gnome. I am not sure. ..

---

### Post by ant2 on 2013-08-10
I'm fairly sure you can use Thunar with Ubuntu 13.04. Not completely sure how to make it default though.

---

### Post by Uncle Spellbinder on 2013-08-11
I'd rather not install another DE. I guess the bottom line is that I do not like the current Nautilus. Particularly that there are only two view modes, list and icons. I miss the third option, compact mode. 

I wonder if Marlin, Nemo or PCManFM can be made the default file manager in Ubuntu.

---

### Post by Uncle Spellbinder on 2013-08-11
I now have the many of the features Nautilus removed back. Added this PPA: [https://launchpad.net/~webupd8team/+archive/experiments](https://launchpad.net/~webupd8team/+archive/experiments)

Added this to my sources.list:
```
### WebUpd8 Patched Nautilus PPA - https://launchpad.net/~webupd8team/+archive/experiments
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb http://ppa.launchpad.net/webupd8team/experiments/ubuntu raring main
```


Then I did:
```
sudo apt-get update
sudo apt-get dist-upgrade
killall nautilus
```

Done. Worked perfectly.

Further, detailed info here: [http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html](http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html)

---

### Post by kurt18947 on 2013-08-11
You may find Nautilus in 13.10 a little better.  Dare we hope the people at Gnome have moderated their minimalist drive a little?  I installed Nemo on another machine and was surprised to see few or no dependencies so that's another option.

---

### Post by Uncle Spellbinder on 2013-08-11
Very good to know about Nemo. Can Nemo be made file manager?

---

### Post by CaptainMark on 2013-08-11
You can install nemo from the cinnamon ppa here [https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable) I think it may pull in the cinnamon DE as a dependency by that doesn't mean you have to use it,

---

### Post by Uncle Spellbinder on 2013-08-11
Thanks. ;)

---

### Post by kurt18947 on 2013-08-11
Nemo is in the Ubuntu repositories.  I don't know if it's the most recent Nemo, some things found in the repositories are a few versions old.  I'm using gnome-shell and Nemo has menus.  I opened Nemo in Unity and there were no menus and it didn't looks as useful.  I only spent a minute in Unity so a cursory glance.  I added Nemo to the gnome-shell launcher so I now have 2 'files' icons but they look different and it's easy to tell the difference.  I'm running 13.10 so repos there may be different than 12.04 etc.

---

