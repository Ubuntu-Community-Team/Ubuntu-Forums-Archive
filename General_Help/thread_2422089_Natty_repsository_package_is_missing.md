---
title: "Natty repsository package is missing ???"
date: 2019-07-02
forum: General Help
---

### Post by Ubuque on 2019-07-02
Hi i am trying to install xscreensaver

apt-cache search xscreensaver returns:

xscreensaver-data - data files to be shared among screensaver frontends
screensaver-default-images - Wallpapers for image processing screensavers
gnome-settings-daemon - daemon handling the GNOME session settings
libpam-gnome-keyring - PAM module to unlock the GNOME keyring upon login
xdg-utils - desktop integration utilities from freedesktop.org
totem-plugins - Plugins for the Totem media player
xscreensaver-gl - GL(Mesa) screen hacks for xscreensaver


but no package called xscreensaver or Xscreensaver ...

---

### Post by CatKiller on 2019-07-02
Natty Narwhal (11.04) ended support in October 2012. Its repositories are long gone.

---

### Post by Autodave on 2019-07-02
18.04 is the newest LTS (long term service).  18 = 2018 and .04 = April.  The next LTS will be 20.04.  You need to download a version of 18.04 and install that.

I normally advise people (especially new users) to stay away from the short term releases since the are usually troublesome.

LTS releases are supported for at least 5 years whereas the short term ones only for 9 months.

---

### Post by Ubuque on 2019-07-02
other packages are missing as well : i think i installed them a few weeks ago..., but am not able to find them anymore, with apt-cache command

like..., is this just an mistake of mine ? the Xserver package however is listed in 

the Contents-amd64.gz file in:

[http://old-releases.ubuntu.com/ubuntu/dists/natty/Contents-amd64.gz](http://old-releases.ubuntu.com/ubuntu/dists/natty/Contents-amd64.gz)

OK, solved, this appeard to be the case due to misconfiguration of my sources.list file.

I had to many sources in .
like natty-security and others.

the packets are in place.

---

### Post by Autodave on 2019-07-02
I don't know.  But, what I do know is that you are using a very old release that no longer should be used.  Time to move up to 18.04.

If you bought a new computer today, would you remove Win10 and install XP on it knowing that support for XP ended a couple years ago?

---

### Post by oldos2er on 2019-07-02
Please don't put the forum community in the unfair position of supporting an OS that Canonical dropped support for seven years ago. Install a supported release, please.

Closed.

---

