---
title: "Sound broke computer"
date: 2007-11-07
forum: General Help
---

### Post by ferrettmerr on 2007-11-07
hey all,
I just recently started fooling around with ubuntu and finally got somewhere with it, until i started to mess with it to much. I tried to get my sound working in 7.10 on my hp pavilion dv9000. I am aware of my compatibility issues, but would like to try and work around it. I do not ahve to worry about any data loss, but would rather not re-install.

i used this guide right before i broke my computer.:

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768) about half way down in the sound section, it starts with

The snd-hda-intel driver is used for sound. It works with the installed version of Feisty, but not after applying all current updates.

With Edgy, internal speakers do not mute when plugging the headphones. A work-around consisted of unchecking the “External Amplifier” box in the sound panel applet, but it caused severe sound degradation. Moreover, it is not the right way to mute the speakers, it just disable an amplifier which causes the loss of quality.

In order to get sound to work properly a manual compile of a patched ALSA is needed (instructions below). alsa-driver-1.0.15 will be patched and then built and installed. Then, alsa-lib-1.0.15 and alsa-utils-1.0.15 will be built and installed too.

libc6-dev required for alsa-driver

sudo apt-get install libc6-dev 

ncurses-dev required for alsa-utils

sudo apt-get install ncurses-dev 

Retrieve and install alsa 1.0.15

mkdir alsa-fix && cd alsa-fix 

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
wget [http://tfc.duke.free.fr/coding/hdaintel-laptop-eapd-hg20070908.patch](http://tfc.duke.free.fr/coding/hdaintel-laptop-eapd-hg20070908.patch)

tar -xvf alsa-driver-1.0.15.tar.bz2
tar -xvf alsa-lib-1.0.15.tar.bz2
tar -xvf alsa-utils-1.0.15.tar.bz2

cd alsa-driver-1.0.15
patch -p1 < ../hdaintel-laptop-eapd-hg20070908.patch
./configure --with-cards=hda-intel --with-sequencer=yes --with-oss=yes
make
sudo make install(theres more)
when it asked for me to put in a cd, i realized i left it home, and decided to try it again later.
Now what would be the way to go around and fix that?
Im thinking either try to run it again in safe mode with the cd, or is there a repair method in Ubuntu?

Thanks for the help.
~ferrettmerr

---

