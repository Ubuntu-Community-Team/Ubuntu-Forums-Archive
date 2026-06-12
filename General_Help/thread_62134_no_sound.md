---
title: "no sound"
date: 2005-09-03
forum: General Help
---

### Post by tktreload on 2005-09-03
Hi I'm having a problem with my sound, there is none

After some exploration i found a section on the forum that describes how to write the file asound.conf, since there was none.
after restarting alsa there is still no sound, but xmms seems to be playing just fine. alsa makes no problems on starting.The only problem that i can find is that there is no sound, and that aplay says:

aplay: set_params:862: Channels count non available

I'm on a 2.6.10-5-686-smp kernel, and the module for the soundcard is intel8x0.
maybe someone has a setup file that i can try or something.

also the alsaconf command is not there...

---

### Post by tktreload on 2005-09-03
also after thinking watching a movie and other things I returened to the problem.
I started thinking where does alsaconf come from, the alsa-utils_1.0.8-1ubuntu_i386.deb package of course.

After checking this package out I found that after doing:
:~$ dpkg -c alsa-utils_1.0.8-1ubuntu1_i386.deb | grep alsaconf
:~$ 

there is nothing... that is to say there is no alsaconf in the package.
on examination of a package from sunsite.dk's mirror of debian (alsa-utils_1.0.8-4_i386.deb) the same command turns out:
rwxr-xr-x root/root     31569 2005-03-04 11:37:44 ./usr/sbin/alsaconf
-rw-r--r-- root/root      1337 2005-03-04 11:37:44 ./usr/share/man/man8/alsaconf.8.gz
-rw-r--r-- root/root      9498 2005-03-04 11:37:44 ./usr/share/locale/ja/LC_MESSAGES/alsaconf.mo

I think there has been an error, and that alsaconf for some reason has not been compiled into the package

---

### Post by d1337 on 2005-09-03
Have you tried [this?](http://www.ubuntuguide.org/#configuresoundproperly)   I have followed these instructions on 4 different machines, all with different hardware, and it has fixed each of them up with no problem.  Just a thought.

d1337

---

### Post by tktreload on 2005-09-04
actually I ended with getting a debian package from sunsite.dk extracting the contents and using alsaconf from there. That also worked. But that does not change that alsaconf is not included in the original ubuntu package...

---

