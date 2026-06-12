---
title: "Why won't Ubuntu 7.10 play mp3's as easily as 7.04 did?!"
date: 2007-12-26
forum: General Help
---

### Post by s3a on 2007-12-26
"Ubuntu 7.10 (Gutsy Gibbon)

    *

      To play some mp3 files in rhythmbox you need to install the w32codecs package from the Medibuntu repository. If you are using the 64 bit version of Ubuntu you will need the w64codecs package instead.
    *

      Some gstreamer players (like Listen) require gstreamer0.10-plugins-ugly"

From:
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)
______________________________________________________________________________
"Ubuntu 7.10
Synaptic

    *

      Go to Applications &#8594; Add/Remove...
    *

      Set Show: to All available applications
    *

      Search for ubuntu-restricted-extras and install it. Note that there is also xubuntu-restricted-extras and kubuntu-restricted-extras.

Or open the Terminal, and execute the following command:

    *

      sudo apt-get install ubuntu-restricted-extras"

From:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
______________________________________________________________________________

"How to add extra repositories, type:
sudo gedit /etc/apt/sources.list
in a terminal and add these lines:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

hit the "save" button in gedit and close it.

Type:
sudo apt-get update
in a terminal and
sudo apt-get install w32codecs"

From:
[http://ubuntuforums.org/showthread.php?t=79449](http://ubuntuforums.org/showthread.php?t=79449)
______________________________________________________________________________
NOTHING SEEMS TO WORK!  :'( HELP ME PLEASE, I WANT TO LISTEN TO MUSIC!!

---

### Post by Tyke91 on 2007-12-26
dunno, mine just did that automatically from the installation (just chose yes to "install appropriate codec")

how did you install 7.10? (did you have an internet connection? are you using 32 or 64 bit?)

---

