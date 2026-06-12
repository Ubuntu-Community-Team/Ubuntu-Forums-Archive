---
title: "hardy and asus a6f: howto"
date: 2008-04-27
forum: General Help
---

### Post by suoko on 2008-04-27
I just FULLY-resolved my audio-related problems of my A6F.

Running:

```
cat /proc/asound/card0/codec#* | grep Codec
```
I got:
Codec: Realtek ALC660
Codec: Motorola Si3054


Then
```
sudo nano /etc/modprobe.d/alsa-base
```
and added

```
options snd-hda-intel enable=1 index=0 model=3stack-660-digout
options snd-hda-intel model=asus-laptop

```

 at the end of the config file. [this is valid if you've got "Codec: Realtek ALC660"]

Restarted the notebook.
Go to system -> preferences -> audio and select "HDA-intel (alsa mixer)

Gnash audio doesn't work (as well as fullscreen mode). Flash does.
I'm now going to test all multimedia app to see how they behave.

KINO, AUDACITY, AVIDEMUX, BANSHEE, OGGCONVERT, SERPENTINE, SOUNDCONVERT, DVDRIP, DVD95, SKYPE and TOTEM work
Still to check gtk-record-mydesktop

[COLOR="Red"]If you still have problems try to do the following:[/COLOR]

By following this [post]("http://toastedtech.wordpress.com/2008/05/16/ubuntu-hardy-e-intel-hda/") here are instructions:

```
sudo apt-get purge alsa-base alsa-utils [it will remove some other packages]
sudo aptitude install   alsa-base alsa-utils fast-user-switch-applet gdm ubuntu-desktop build-essential libncurses-dev gettext linux-headers-`uname -r`

sudo mkdir -p /usr/src/alsa
cd  /usr/src/alsa
sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
sudo wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)
sudo wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)

sudo tar xjvf alsa-driver-1.0.16.tar.bz2
sudo tar xjvf alsa-lib-1.0.16.tar.bz2
sudo tar xjvf alsa-utils-1.0.16.tar.bz2

cd alsa-driver-1.0.16
sudo ./configure --with-cards=hda-intel && sudo make && sudo make install

cd alsa-lib-1.0.16
sudo ./configure && sudo make && sudo make install

cd alsa-utils-1.0.16
sudo ./configure && sudo make && sudo make install
```

---

