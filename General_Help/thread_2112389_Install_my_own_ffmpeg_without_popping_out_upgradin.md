---
title: "Install my own ffmpeg without popping out upgrading info."
date: 2013-02-04
forum: General Help
---

### Post by jiapei100 on 2013-02-04
Hi, all:

I installed ffmpeg from source. I seriously don't like the version of ffmpeg from current repository of Ubuntu 12.10 . I even specified a higher version number of my own ffmpeg. However, still, Ubuntu 12.10 frequently reports and asks me to upgrade my ffmpeg. 

Is there a method that I can avoid such upgrading notification for a particular package? I mean, maybe I'd love some other packages to be upgraded, but not this particular one "ffmpeg" ?


Cheers
Pei

---

### Post by Yellow Pasque on 2013-02-04
[https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages](https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages)

---

### Post by UltimateCat on 2013-02-04
Hi:

I looked up "alternatives to ffmpeg" and found a few articles-
Hope this helps-

[http://stackoverflow.com/questions/6081045/alternative-to-ffmpeg-for-dynamically-creating-video-thumbnails](http://stackoverflow.com/questions/6081045/alternative-to-ffmpeg-for-dynamically-creating-video-thumbnails)

[http://stackoverflow.com/questions/9327264/alternative-to-ffmpeg-for-ios](http://stackoverflow.com/questions/9327264/alternative-to-ffmpeg-for-ios)

[http://drupal.org/node/127212](http://drupal.org/node/127212)

And here are other freeware applications and other alternatives to choose from:
[http://www.techsupportalert.com/](http://www.techsupportalert.com/)

I don't think there is another method where you could avoid upgrading-

---

### Post by andrew.46 on 2013-02-04
Have a look at the use of checkinstall here:

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

Specifically the *--pkgversion* option...

---

### Post by FakeOutdoorsman on 2013-02-04
The important number, last I checked, is the epoch: [Debian Policy Manual](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version). You can probably use an arbitrarily high number or cross-reference a [package search](http://packages.ubuntu.com/quantal/ffmpeg) and use a value that is at least one number higher.

```
--pkgversion="**[color=#FF6600]7[/color]**:$(date +%Y%m%d%H%M)-git"
```

---

### Post by SeijiSensei on 2013-02-04
Isn't the easiest solution to install to /usr/local with "sudo make install", then remove the repository version with "sudo apt-get remove ffmpeg"?  Then there won't be a package for the system to try and update.

---

### Post by Yellow Pasque on 2013-02-04
> Isn't the easiest solution to install to /usr/local with "sudo make install", then remove the repository version with "sudo apt-get remove ffmpeg"? Then there won't be a package for the system to try and update.
Except then all the packages that depend on ffmpeg get removed too... The checkinstall method is probably the best idea.

---

### Post by SeijiSensei on 2013-02-04
OK, that makes sense, though I have to say I find that aspect of package management on Ubuntu annoying.  I encounter it from time to time when I want to remove a package temporarily for whatever reason and suddenly a dozen other packages are removed as well.  Looking at the man page for apt-get I don't see any way to override this behavior either.

My other solution in these cases is simply to leave the package installed knowing that /usr/local/bin precedes /usr/bin in my PATH.  So if I install to /usr/local, I'll get my compiled version regardless of whether it also exists as a package.  I've done this lately with mplayer2, where my copy of smplayer has /usr/local/bin/mplayer as the player path.  The attraction of this approach is being able to compare the behavior of the two programs just by specifying the full path at the command prompt.

---

### Post by mc4man on 2013-02-04
for a static build the instructions here should produce a ffmpeg package that will not be seen as an upgrade to whatever your Ubuntu release's ffmpeg package is providing (may just be some symlinks to avconv, ect.
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

With checkinstall you can also name it whatever you want & or install to /opt  (for standalone or other specific purposes the package does not need to be named just "ffmpeg", nor does the binary need to be named ffmpeg

---

### Post by jiapei100 on 2013-02-04
Fantastic....

Thank you...


Cheers
Pei

> **Temüjin said:**
> [https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages](https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages)

---

