---
title: "Unmet dependencies Installing Miro"
date: 2014-08-01
forum: General Help
---

### Post by darragh-0 on 2014-08-01
Hi, 
I'm really new to ubuntu and Linux in general so i normally manage to hamfistedly find my way round problems using thread on here and using my old friend google but for this one i'm completely lost.

I'm trying to install Miro and i keep getting the following error message:

 libtorrent-rasterbar6 : Depends: libboost-system1.49.0 (>= 1.49.0-1) but it is not installable
 miro : Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not installable
        Depends: python-support (>= 0.90.0) but it is not installable
        Depends: python-gnome2 but it is not installable
        Depends: python-gst0.10 but it is not installable
        Depends: python-libtorrent but it is not installable
        Depends: python-mutagen but it is not installable
        Depends: python-webkit but it is not installable
        Depends: libavahi-compat-libdnssd1 but it is not installable
        Depends: ffmpeg but it is not installable
        Depends: ffmpeg2theora but it is not installable
        Depends: miro-data (= 6.0-1ubuntu1~ppa2~precise) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



Any help would be greatly appreciated. Thanks.

---

### Post by mc4man on 2014-08-01
Your issue  may be right at the top, libtorrent-rasterbar6
what does this show - 
```
apt-cache policy libtorrent-rasterbar6
```
Are you using precise (12.04)? (the dep on libtorrent-rasterbar6 is for the 13.04 version

---

### Post by darragh-0 on 2014-08-01
I get:

libtorrent-rasterbar6:
  Installed: 0.16.3-0ubuntu1
  Candidate: 0.16.3-0ubuntu1
  Version table:
 *** 0.16.3-0ubuntu1 0
        100 /var/lib/dpkg/status


And i'm using 13.04.

---

### Post by mc4man on 2014-08-01
13.04 is EOL (end of life) so the 'normal' repos are gone. That's why nothing new can be installed. 
So you could consider going to 14.04 or if wishing to stick with 13.04 then you'll need to enable the old-release repos in one way or the other.

see here  for some links [http://ubuntuforums.org/showthread.php?t=2235128&p=13079521&viewfull=1#post13079521](http://ubuntuforums.org/showthread.php?t=2235128&p=13079521&viewfull=1#post13079521)

---

### Post by darragh-0 on 2014-08-01
Ok. Thanks a million for the help. I'll give 14.04 a go and see how i get on it.

---

