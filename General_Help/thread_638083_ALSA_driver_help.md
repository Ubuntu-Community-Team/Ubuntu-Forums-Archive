---
title: "ALSA driver help"
date: 2007-12-11
forum: General Help
---

### Post by jsprung on 2007-12-11
Hey all,
I'm a new ubuntu user. So far i love it, but there have been some problems. Among them is the fact that I have no sound. My soundcard is an EMU 1212m, which theoretically is compatible with Linux via the ALSA drivers. I have installed a bunch of ALSA packages through synaptic, but still have no sound. I tried following these instructions, [http://www.alsa-project.org/main/index.php/Matrix:Module-em](http://www.alsa-project.org/main/index.php/Matrix:Module-em), but I can't for the life of me. Can anyone give me some advice on how to get my card up and running?

---

### Post by Pumalite on 2007-12-11
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure 
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot

---

### Post by jsprung on 2007-12-11
thanks a lot for the help. when I try to download the three files, it is saying "No such file `utils...1.0.15.tar.bz2'" for each. perhaps they have been moved?

---

### Post by jsprung on 2007-12-11
never mind, figured it out.

---

### Post by jsprung on 2007-12-11
So i followed the above steps and restarted my computer, but...now it won't start. It says it has an error loading the hardware drivers with EMU101k_audigy.

---

### Post by Pumalite on 2007-12-11
From prior posts (select your solution. You can try all this in Recovery Mode):
Note: Initially, because I had fiddled with it so much, I had nothing detected - a red X next to the volume control, would tell me I had no sound card when I tried to adjust volume. To get rid of that, I ran "sudo apt-get install linux-backports-modules-generic" as suggested by Pumalite, and it restored it to (what appears to be) the default - sound card looks like it's working, but you can't hear sound out of anything.

 Re: [SOLVED] No sound after installation of Gutsy
I have finally solved the problem after a lot of playing around. The answer was very simple - go to the volume control icon in the right hand corner of the screen, open the Alsa mixer, select the switches tab and uncheck the 'Audigy Analog/Digital Output Jack' option. This must be happening to a lot of people trying Ubuntu for the first time. Does anyone know why this is selected on as Default? Surely most people use analogue speakers as default? As always thanks for the help.

 Re: [SOLVED] No sound after installation of Gutsy
What are you saying for analog digital jack its true..This must be unchecked..Im guessing alsa doesnt support it.
As for the other problem i solved it by:
Getting the list of sound cards
Quote:
sudo asoundconf list
Setting as default the one i want
Quote:
asoundconf set-default-card soundcard
Replacing soundcard with mine
And i used this command to test my surround 5.1:
Quote:
speaker-test -D surround51 -c 6
which after some digging on volume control and enabling from preferences new menus i manage to get it to work
__________________

---

### Post by jsprung on 2007-12-11
I get the same error when attempting to start in Recovery Mode.

---

### Post by jsprung on 2007-12-19
My computer still won't start...

---

