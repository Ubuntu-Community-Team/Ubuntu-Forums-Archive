---
title: "Playing Movies"
date: 2005-07-05
forum: General Help
---

### Post by techbeck on 2005-07-05
Ok, I am a linux idiot...so be for warned....

I am trying to play movies and it saying i donthave the correct codecs or whatever.  So I tried to download/install VIDEOLAN software.  Works pretty good on Windows so I thought i would try it here.  Cant get thing to install.   I follow the instructions fora debian install and nothing happens.

Any ideas on getting movies to play??

thanks!!

---

### Post by jasmuz on 2005-07-05
[QUOTE=techbeck]Ok, I am a linux idiot...so be for warned....

I am trying to play movies and it saying i donthave the correct codecs or whatever.  So I tried to download/install VIDEOLAN software.  Works pretty good on Windows so I thought i would try it here.  Cant get thing to install.   I follow the instructions fora debian install and nothing happens.

Any ideas on getting movies to play??

thanks!![/QUOTE]
 Sure..

First of, add these repositories to your sources.list, like this: sudo gedit /etc/apt/sources.list

This is what you are going to add (just copy-paste it):

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Now you must save and close, then on the console type: sudo apt-get update

Now we are going to install a video player, either Xine or Mplayer
Like so, 

sudo apt-get install xine-ui
sudo apt-get install mplayer mplayer-fonts

If you want extra codecs to play movies (and have a fast internet connection)

sudo apt-get install w32codecs

That should get you going!

---

### Post by techbeck on 2005-07-05
Tried that, this is what i get after i type sudo apt-get update.  i edited the file like you said.


someone@technix:~$ sudo apt-get install mplayer mplayer-fonts
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer
someone@technix:~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate

---

### Post by jasmuz on 2005-07-05
Well, i will have to ask you to copy all these to your sources list, so you can have the proper packages.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

#Backup Mirror - SLOW
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Remove all from your list and place these.
then do a sudo apt-get update
and install the packages i mentioned earlier.

---

### Post by techbeck on 2005-07-05
thanx, i had to update a bunch of stuff...working now!!

---

### Post by jasmuz on 2005-07-05
[QUOTE=techbeck]thanx, i had to update a bunch of stuff...working now!![/QUOTE]
 Great!

---

