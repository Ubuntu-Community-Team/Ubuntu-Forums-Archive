---
title: "Cannot playback WMV files!"
date: 2005-10-02
forum: General Help
---

### Post by Panthios on 2005-10-02
Hi.

I don'tunderstand, I cannot play WMV files. Xine says an error about scrample media. Mplayer shows the file, but only green screen.

I have w32codecs installed from ftp.nerim.net source and everthing from:
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) - except gstreamer8.0-lame and libdivx4linux - it says that it could not found that packages.

:confused: :confused: 

My sources.list:

```
deb http://dk.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu hoary main restricted

deb http://dk.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://dk.archive.ubuntu.com/ubuntu hoary universe
deb-src http://dk.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

##########################
##########################

# Codecs
#deb ftp://ftp.nerim.net/debian-marillat/ sarge main

```


Running Kubuntu

---

### Post by tseliot on 2005-10-02
If you use Kubuntu 64bit wmv9 won't play, if this is not your case I don't know how to help you.

---

### Post by Panthios on 2005-10-02
Nope, it's not 64bit. I don't understand either.
I have never had problem before installing codecs/playing WMV files.
Im quite confused :???:

---

### Post by Panthios on 2005-10-02
Oh well, I just wait till Breezer goes stable and I will try again.
But still, it kinda s.... :(

---

### Post by Hairy_Palms on 2005-10-02
its gstreamer0.8-lame not 8.0 and libdivxisnt there and isnt needed, what i found to work was installing totem-xine and use totem,

---

