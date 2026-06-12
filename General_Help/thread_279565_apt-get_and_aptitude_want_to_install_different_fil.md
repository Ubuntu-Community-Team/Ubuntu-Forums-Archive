---
title: "apt-get and aptitude want to install different files"
date: 2006-10-18
forum: General Help
---

### Post by tintax on 2006-10-18
I've recently installed the Xubuntu Edgy Beta. I'm really quite fond of gedit (can't find a purely GTK app to equal it) so I went to install it via aptitude and it wanted to install several packages that didn't make much sense to me (e.g. gstreamer). No idea why I tried it, but asking apt-get to install it gives me a smaller list of dependencies (and no gstreamer).

Does anyone know:

[LIST=1]
[*]Why these utilities want to install different packages?
[*]If I can persuade aptitude not to install certain dependencies?
[/LIST]

For your information:

```
$ sudo aptitude install gedit

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  openoffice.org-common openoffice.org-core openoffice.org-help-en-us 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za 
The following NEW packages will be automatically installed:
  gedit-common gnome-media gnome-media-common gstreamer0.10-alsa 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x 
  libcdio6 libgail-common libgail18 libgnome-media0 libgtksourceview-common 
  libgtksourceview1.0-0 libiec61883-0 libmetacity0 libnautilus-burn4 
  liboil0.3 libpanel-applet2-0 libshout3 libvisual-0.4-0 
  libvisual-0.4-plugins libwnck-common libwnck18 libxres1 metacity-common 
  python-gnome2-desktop python-pyorbit 
The following packages have been kept back:
  dhcp3-client dhcp3-common gaim gaim-data initramfs-tools libscim8c2a 
  python-central scim scim-gtk2-immodule scim-modules-socket 
  system-tools-backends ubuntu-minimal update-manager usplash x11-common 
  xbase-clients xorg xserver-xorg xserver-xorg-input-all 
  xserver-xorg-video-all xubuntu-desktop xubuntu-system-tools xutils 
The following NEW packages will be installed:
  gedit gedit-common gnome-media gnome-media-common gstreamer0.10-alsa 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x 
  libcdio6 libgail-common libgail18 libgnome-media0 libgtksourceview-common 
  libgtksourceview1.0-0 libiec61883-0 libmetacity0 libnautilus-burn4 
  liboil0.3 libpanel-applet2-0 libshout3 libvisual-0.4-0 
  libvisual-0.4-plugins libwnck-common libwnck18 libxres1 metacity-common 
  python-gnome2-desktop python-pyorbit 
0 packages upgraded, 28 newly installed, 0 to remove and 28 not upgraded.
Need to get 7893kB of archives. After unpacking 52.1MB will be used.
Do you want to continue? [Y/n/?] n
```

```
$ sudo apt-get install gedit

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gedit-common gnome-media-common libgnome-media0 libgtksourceview-common
  libgtksourceview1.0-0 libmetacity0 libnautilus-burn4 libpanel-applet2-0
  libwnck-common libwnck18 libxres1 metacity-common python-gnome2-desktop
  python-pyorbit
Suggested packages:
  python-gnome2-desktop-doc
Recommended packages:
  gnome-media
The following NEW packages will be installed:
  gedit gedit-common gnome-media-common libgnome-media0
  libgtksourceview-common libgtksourceview1.0-0 libmetacity0 libnautilus-burn4
  libpanel-applet2-0 libwnck-common libwnck18 libxres1 metacity-common
  python-gnome2-desktop python-pyorbit
0 upgraded, 15 newly installed, 0 to remove and 14 not upgraded.
Need to get 5599kB of archives.
After unpacking 44.5MB of additional disk space will be used.
Do you want to continue [Y/n]? n
```

---

### Post by hw-tph on 2006-10-18
aptitude will install suggested packages as well as the packages the dependancies require. If you run the aptitude shell program you are able to deselect the suggested packages from the list of packages to install.


Håkan

---

### Post by anaconda on 2006-10-18
Is there still the same difference after you type:
sudo aptitude update
sudo apt-get update

and try again?

interesting..

---

### Post by tintax on 2006-10-18
Thanks for that hw-tph - running it interactively did give me the option to ignore those packages. Which, in turn, encouraged me to have another look at the man page:

```
       -R, --without-recommends
              Do not treat recommendations as dependencies when installing new packages  (this  overrides  settings  in  /etc/apt/apt.conf  and              ~/.aptitude/config). This corresponds to the  configuration  option  Aptitude::Recom&#8208;mends-Important
```

therefore sudo aptitude install -R gedit is what I needed.

Sorry anaconda, I should have mentioned that I did run update before trying the install commands. Thanks for taking the time to help though.

---

### Post by hw-tph on 2006-10-18
Oh well, I was too lazy to read up on the man page so I'm glad you did it. Now we both know -R skips the recommended packages. :)


Håkan

---

### Post by Malakia on 2006-10-18
Aptitude is also nice when you remove files because it will remove all the dependecies with it. With apt-get it will only remove the file that you specify.

---

### Post by meng on 2006-10-18
Slight correction: aptitude will remove those dependencies not required by other installed packages. (You wouldn't really want it to remove ALL dependencies, now, would you?)

---

### Post by tintax on 2006-10-19
> **meng said:**
> Slight correction: aptitude will remove those dependencies not required by other installed packages. (You wouldn't really want it to remove ALL dependencies, now, would you?)

Yes indeed, that is why I wanted to install via aptitude in the first place. I just didn't want pointless packages.

It's bad enough that I much prefer XFCE (my other OS is gentoo) but feel I can't live without exactly one gnome app (gedit for web dev) and exactly one KDE app (kaffeine for DVB).

Sigh.

---

### Post by Funk Soul Brother on 2006-11-11
Ok - here comes a dumb question from a total Mac OS X addict getting treatment. Does a particular package only work on a particular desktop? Say - gedit only works on gnome? Arrgghh.

---

### Post by ciscosurfer on 2006-11-11
Typically no.  Providing you have the essentials for each DE (and even if you don't, you're still okay, things might just look a little funky -- let's say you normally run KDE, and want to install GEdit, if you do it through Aptitude, it will grab the necessary files for you.  The same occurs if you run Gnome and want to download Kaffeine, for example).

I run many KDE apps from within Gnome and many Gnome apps from within KDE -- everything works great.

---

### Post by aysiu on 2006-11-11
*aptitude* tries to "smartly" handle dependency issues. Sometimes it's a little too "smart" for its own good. So I generally advise using *aptitude*, but if it acts up, I use *apt-get* instead for situations like these.

Sometimes *aptitude* acting up has to do with a bad repositories list with conflicting sources or too many sources.

---

### Post by Funk Soul Brother on 2006-11-11
Thanks, ciscosurfer. You rock, dude.

---

### Post by Funk Soul Brother on 2006-11-18
Thanks, ciscosurfer. You rock.

---

### Post by ciscosurfer on 2006-11-19
Sure!  Any time, Mr. Funk Soul Brother!

---

