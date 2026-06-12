---
title: "Critical errors with sound in 7.10"
date: 2007-12-05
forum: General Help
---

### Post by Eoset on 2007-12-05
Godmorning, I have a problem which seems to happend to others then just me. Installed the latest compiz fuzion thingies and then my sound disappeared. Getting an error in the Properties for sound dialog which reads: _audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing._

My soundcard cant be located in that dialog either

I was foolish enough in the desperate need of sound so use a script which probably wasn´t the smartest idea I´v had...

The script was supposed to make your sound work if u had a certain board which I apparently hadn´t.

What should I do? Iv quite new to the whole Linux world so Im not an experienced user. Any help and suggestions are welcome!

Also adding the script I used to see if anyone got any ideas on what I should do.

[I]#!/bin/bash
sudo apt-get install build-essential ncurses-dev gettext libncurses5-dev linux-headers-`uname -r`
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
sudo wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
sudo wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
sudo rm alsa-driver-1.0.15.tar.bz2
sudo rm alsa-lib-1.0.15.tar.bz2
sudo rm alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
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
sudo echo "options snd-hda-intel model=toshiba position_fix=0 enable=yes
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss" | sudo tee -a /etc/modprobe.d/alsa-base
sudo mv /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
sudo depmod -a
sudo reboot[/I]

Best Regards
Erik Sällström
[www.ist.com]("http://www.ist.com")

---

### Post by gobbles414 on 2007-12-05
Hi Eoset,

Usually Ubuntu offers at least two sound choices -- Alsa and OSS. Have you tried switching from one of these to the other? One of the many ways that you can accomplish that is by going *System => Preferences => Sound => Device*.

---

