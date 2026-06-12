---
title: "ROAP Play, Alsa, Kernel and Build Problem"
date: 2007-03-28
forum: General Help
---

### Post by DoctorMO on 2007-03-28
Hello all,

I tried to install kaop-play from [http://raop-play.sourceforge.net/](http://raop-play.sourceforge.net/) to use the airport airtunes to route sound.

Now the software programs install fine, but they do nothing for using amarok or other software to play music, videos and other things.

the problem is that when I go into drivers/ and run make I got an error that the build directory want found. a bit of investigation shows the build directory under /lib/modules/2.6.17-11-generic instead of /lib/modules/2.6.17-11-386 so I link build from generic to 386 and can now make the ko file.

Now the problem comes, with the roap-alsa module installed I get the following error when I try to add the module:

FATAL: Error inserting alsa_raoppcm (/lib/modules/2.6.17-11-386/sound/alsa_raoppcm.ko): Invalid module format

This seems a bit pants that it can't even make a valid module using ubuntus own build directory, must be something I'm doing wrong. does anyone know anything about building kernel modules?

---

### Post by DoctorMO on 2007-03-28
Solution found, wrong kernel headers installed. had 2.6.17.10 installed when an update must have brought it up to 2.6.17.11, removing the old headers and installing the news ones and a recompile and install worked perfectly.

---

