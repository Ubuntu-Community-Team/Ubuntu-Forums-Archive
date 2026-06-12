---
title: "Display controls for firefox mplayer plugin?"
date: 2005-04-24
forum: General Help
---

### Post by jaegen on 2005-04-24
Hello,

I have the mplayer plugin working in firefox just fine, however there are no controls to pause/restart etc.  The video just plays, and if I want to replay it I have to refresh the page.  Is there any way to display controls for this?

On a related note, given that I can't control playback using mplayer, I've installed the VLC plugin for firefox.  However, firefox is still using the mplayer plugin to play videos.  Is there a way of changing which plugin firefox uses if there are multiple plugins for the same file type?  Or can I temporarily disable the mplayer plugin without uninstalling it?

Thanks,

Jaegen

---

### Post by Knome_fan on 2005-04-24
The problem is that mplayer plugin isn't build with gtk2 (it's not even build with plain old gtk).
So, in order to get the controls you'll have to rebuild the package using gtk2.

To do this simply get the source with apt-get source mozilla-mplayer, then edit debian/rules in the mplayerplug-in directory and change --enable-x to --enable-gtk2 and rebuild the package with dpkg-buildpkg.

Have fun!

---

### Post by jaegen on 2005-04-26
What repository is the source package in?  I'm getting this:

```
$ sudo apt-get source mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for mplayerplug-in

```

I thought I had all the source repositories available.  Here are all the non-comment lines in my souces.list file

```
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
```

---

### Post by Knome_fan on 2005-04-26
It should be in multiverse and I think you are missing the multiverse source repository, just add it and it should work.

---

### Post by pimpaulogy on 2007-11-06
Does anybody have a "how to" on fixing this?

I have just did a fresh install of gutsy, used the Ubuntu guide to get most of my apps up and running ([http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)),

but I still have this issue and I am a newbie when it comes to Linux.

Thanks in advance for the help.

---

