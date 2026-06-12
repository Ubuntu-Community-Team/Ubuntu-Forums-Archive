---
title: "totem-xine can't read video"
date: 2005-05-16
forum: General Help
---

### Post by arkal on 2005-05-16
Hey! I can't read video and mp3 files
So I read about it and I tried to install w32codecs, but it seems it can't be downloaded from sudo apt-get install w3codecs...

Anyone can help me?
Thanks 


Arkal

---

### Post by bored2k on 2005-05-16
[QUOTE=arkal]Hey! I can't read video and mp3 files
So I read about it and I tried to install w32codecs, but it seems it can't be downloaded from sudo apt-get install w3codecs...[/QUOTE]
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

That's the right way to get codecs ;).

---

### Post by agds on 2005-05-16
If you configure Synaptic to use Hoary-extras as one of its repositories, you should be able to install the package that way.  More info can be found at [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) in the appropriate section.

---

### Post by arkal on 2005-05-16
I tried the guide, but it can't download all those files because it don't find them...

---

### Post by bored2k on 2005-05-16
[QUOTE=arkal]I tried the guide, but it can't download all those files because it don't find them...[/QUOTE]
 Ok.. You can try following ubuntu-geek's automatic script here [it will do this and several other cool tweaks]:

```
Open a terminal session and enter:
wget http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh
sudo sh ubuntusetup.sh
```
You will be asked to select "Yes" or "No" on various things you will want to select yes on them.

> Purpose: To automate installation of the following programs because I am lazy and hate selecting to install them manually after I format my computer (which is often) so this script saves me alot of time and I hope it helps you too.

build-essential - Compilers needed to build programs
beep-media-player - XMMS gtk2 clone. Compatible with XMMS plugins/skins
gstreamer0.8-mad - Add MP3 support for Rhythmbox
w32codecs - Windows codecs for playing various files
streamtuner - Online music streamer from shoutcast and a few others
xine-ui - The xine video player, user interface for playing dvd's and such
totem-xine - Have totem use xine so you can actually use it to play videos etc.
msttcorefonts - Windows True Type Fonts
acroread - Latest version of Adobe Acrobat Reader
acroread-plugin - Firefox Acobat Reader Plugin
libdvdcss2 - DVD Library
gnomebaker - The best gnome/gtk2 cd/dvd/cdrw burning software
gftp - Ftp Client
flashplayer-mozilla - Flash plugin for firefox
Java JRE 1.5 - Latest version of Java
Custom Firefox Forms - Make you firefox form widgets look decent
/etc/apt/sources.list - Add in universe, multiverse and misc repositories
Misc Windows Fonts - Misc fonts that are missing in the msttcorefonts package

---

