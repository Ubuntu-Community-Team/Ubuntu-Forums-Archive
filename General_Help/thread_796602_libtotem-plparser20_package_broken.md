---
title: "libtotem-plparser20 package broken?"
date: 2008-05-16
forum: General Help
---

### Post by BigErn on 2008-05-16
I just did my usual apt-get full-upgrade today and I get this:

root@deathvalley:/home/danahata# aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libtotem-plparser10 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.8kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libtotem-plparser10: Depends: libcamel1.2-11 (>= 2.22.1.1) but 2.22.1-0ubuntu2.1 is installed.
                       Depends: libedataserver1.2-9 (>= 2.22.1.1) but 2.22.1-0ubuntu2.1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
brasero
deskbar-applet
gnome-applets
gnome-games
gnome-games-data
gnome-volume-manager
libdeskbar-tracker
libtotem-plparser10
python-gnome2-desktop
rhythmbox
totem
totem-gstreamer
totem-mozilla
totem-plugins
ubuntu-desktop

Downgrade the following packages:
gnome-panel [1:2.22.1.3-0ubuntu1 (hardy-updates, now) -> 1:2.22.1.2-0ubuntu3 (hardy)]

Leave the following dependencies unresolved:
gnome-panel recommends gnome-applets (>= 2.12.1-1)
Score is 915

Accept this solution? [Y/n/q/?]

---

### Post by monstermudder78 on 2008-05-16
I think your title should say: libtotem-plparser**10** package broken?

But I too am having this problem and I'm not sure what to do about it.  Anyone?

---

### Post by Ragnar Bocephus on 2008-05-16
Same problem here.  I'm guessing it's one of those things that will be sorted out in a day or two.

---

### Post by Scollardical on 2008-05-16
I encountered the same thing. I didn't see any message about it being broken but now the libtotem-plpparser10 package remains in update manager only it is grayed out.

I guess it will get fixed at some point.

---

### Post by gotee12 on 2008-05-16
If I try to force the upgrade in Synaptic, it gives me an error about two packages...

```
libtotem-plparser10:
  Depends: libcamel1.2-11 (>=2.22.1.1) but 2.22.1-0ubuntu2.1 is to be installed
  Depends: libedataserver1.2-9 (>=2.22.1.1) but 2.22.1-0ubuntu2.1 is to be installed
```

...it looks like a dependency issue. As in libtotem is requiring a newer version of the other two libraries than what's currently available (at least that's the way I read it). 

As everyone else has said, give it a day or two and it'll all get sorted out.

---

### Post by jdunn on 2008-05-17
> **Ragnar Bocephus said:**
> Same problem here.  I'm guessing it's one of those things that will be sorted out in a day or two.

Same problem here with libtotem-plparser10

---

### Post by Muflon on 2008-05-17
Same problem here on both my laptops!

---

### Post by Xiong Chiamiov on 2008-05-17
Yes, but aptitude just holds it back.

It's rather annoying having adept updater stay in my system tray.

---

### Post by BigSilly on 2008-05-17
My updates came through this morning, and this package was part of it. Oddly, it wouldn't update it, and the item is greyed out in Update Manager. Perhaps the Ubuntu team spotted the problems early on and have stopped it updating until it's fixed? Whatever, but I'm glad it didn't update to it anyway. Thanks for the heads up here folks.

---

### Post by frodon on 2008-05-17
Same here, this sound like a mistake uploading new packages in repositories, should be fixed soon, if not then we should fill a bug report.

EDIT: Bug report filled [https://bugs.launchpad.net/ubuntu/+bug/231361](https://bugs.launchpad.net/ubuntu/+bug/231361), feel free to comment it.

---

### Post by Scollardical on 2008-05-17
This seems to be fixed now. I did an update and the package was available to apply.

---

### Post by axle_foley00 on 2008-05-17
I am also having this issue. Update Manager just hangs when I tell it to install the packages.

**Edit:** It seems when I do 'sudo apt-get upgrade' I was now able to upgrade those packages. It wasn't working through the graphical Update Manager before though.

---

### Post by rmksd on 2008-05-17
> root@RMKSD:/home/ken# aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  libtotem-plparser10 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.8kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libtotem-plparser10: Depends: libcamel1.2-11 (>= 2.22.1.1) but 2.22.1-0ubuntu2.1 is installed.
                       Depends: libedataserver1.2-9 (>= 2.22.1.1) but 2.22.1-0ubuntu2.1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
avant-window-navigator
awn-manager
brasero
deskbar-applet
gmail-notify
gnome-applets
gnome-games
gnome-games-data
gnome-volume-manager
libdeskbar-tracker
libtotem-plparser10
python-gnome2-desktop
python-gnome2-extras
rhythmbox
screenlets
totem
totem-gstreamer
totem-mozilla
totem-plugins
ubuntu-desktop
xubuntu-desktop

Downgrade the following packages:
gnome-panel [1:2.22.1.3-0ubuntu1 (hardy-updates, now) -> 1:2.22.1.2-0ubuntu3
(hardy)]

Leave the following dependencies unresolved:
gnome-panel recommends gnome-applets (>= 2.12.1-1)
Score is 611


im still sort of a newbie at all of this but from the looks of it i have to get rid of all of those -possibly losing settings and yadda yadda.. and then i get have a problem free plparser? ugh:mad:

---

