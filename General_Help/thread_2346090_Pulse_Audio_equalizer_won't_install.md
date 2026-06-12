---
title: "Pulse Audio equalizer won't install"
date: 2016-12-11
forum: General Help
---

### Post by cheapodonuts on 2016-12-11
I followed the instructions on this site [https://www.maketecheasier.com/pulse-audio-equalizer-ubuntu/](https://www.maketecheasier.com/pulse-audio-equalizer-ubuntu/)

but ended up with this :

W: The repository 'http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu/dists/yakkety/main/binary-amd64/Packages](http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu/dists/yakkety/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.


Do I need a different version for Studio or something? 


Currently listening to Gary Moore

:guitar:

---

### Post by jeremy31 on 2016-12-11
See if the one mentioned in the webupd8 [article](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html) works

---

### Post by Yellow Pasque on 2016-12-11
I'd think I'd prefer the official pulseaudio equalizer ('qpaeq'): [http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)
It's really not that much more difficult to setup if you can follow instructions and have basic familiarity with command line.

---

### Post by cheapodonuts on 2016-12-11
Thanx guys. But I get the same result from those as well.  Maybe it's because my system is actually 16.10 and not 16.04. This forum doesn't seem to allow me to show that.
.
Ok, found it now.  :redface:

---

