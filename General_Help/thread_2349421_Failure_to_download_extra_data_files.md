---
title: "Failure to download extra data files"
date: 2017-01-14
forum: General Help
---

### Post by eddiefiggie on 2017-01-14
Hello!

I am using UBUNTU 16.04...have had no issues, but recently I get the error message in a pop-up box indicated in the subject line.  Reading the pop-up box it articulates that "ttf-mscorefonts-installer" is the culprit.  Sounds like something to do with my WINE setup?  perhaps it is calling a file that isn't there?  *shrugs*

Thought maybe one of you hear can point me to a solution...  Tired of seeing this pop-up.

The pop-up box has a RUN THIS ACTION NOW button...  After pushing it it will prompt me for the admin password as you might expect...  Doesn't seem to solve the issue.  The box just returns.

I've just been ignoring it...hehe  But it is quite annoying at this point.

HELP!  =)

---

### Post by howefield on 2017-01-14
The 3.4 version of the ttf-mecorefonts-installer package is broken.

Sourceforge (where the actual font files are downloaded from) changed the location that the fonts are stored rendering the package broken. I'd suggest purging that broken 3.4 version of the package and instead install the 3.6 version of the package from an alternative source, eg

```
sudo apt purge ttf-mscorefonts-installer
```

to get rid of the current package

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

to download the 3.6 version of the package to your Downloads folder, and

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

to install the new package.

---

### Post by eddiefiggie on 2017-01-14
That was it.

Thanks!

---

### Post by howefield on 2017-01-14
You're welcome and thanks for marking the thread as solved.

---

### Post by Geoffrey_Arndt on 2017-01-15
Same problem here . . . . same fix also.    Thanks Howefield . . . I wonder for how many other folks that this issue was/is also a major annoyance.   Casual users will have no idea what to do.

---

### Post by howefield on 2017-01-16
> **Geoffrey_Arndt said:**
> Same problem here . . . . same fix also.    Thanks Howefield . . . I wonder for how many other folks that this issue was/is also a major annoyance.   Casual users will have no idea what to do.

You're very welcome, I *think* that [this is the bug]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1651923") that will fix it, albeit some time yet before it hits 16.04 and 16.10, until then I'll just keep using the 3.6 version.

---

### Post by bigguns2 on 2017-01-18
Same trouble here, and again this fixed it. Thanks

---

