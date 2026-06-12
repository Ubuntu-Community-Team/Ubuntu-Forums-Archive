---
title: "Can't get video thumbnails in Thunar"
date: 2013-04-16
forum: General Help
---

### Post by Sam Mills on 2013-04-16
I've tried everything I can find, but still can't get video thumbnails in thunar. Tumbler and ffmpegthumbnailers are installed. Thanks.

---

### Post by nerdtron on 2013-04-16
I'm using Thunar in Xfce and video thumbnails are not shown either. I think this is by design since Xfce is for low resource machine.

---

### Post by Sam Mills on 2013-04-16
> **nerdtron said:**
> I'm using Thunar in Xfce and video thumbnails are not shown either. I think this is by design since Xfce is for low resource machine.
Actually, xfce is for anyone who enjoys that DE. I don't think it's necessarily just for low resource machines. But thanks anyway, I'm sure there must be a way to do it.

---

### Post by nerdtron on 2013-04-16
You're right about that. I enjoy using Xfce more than any other DE. And now your post made me curious for I tried searching and installing tumbler, tumbler-plugins-extra and ffmpegthumbnailers and still no luck :/

---

### Post by tdockery97 on 2013-04-16
One I didn't see you mention that may or may not help.  Try installing ffmpegthumbs (it's a different package than thumbnailer).

---

### Post by Sam Mills on 2013-04-16
> **tdockery97 said:**
> One I didn't see you mention that may or may not help.  Try installing ffmpegthumbs (it's a different package than thumbnailer).

Thanks, tried that but still nothing.

---

### Post by Sam Mills on 2013-04-16
Trust me, I'm scouring google and forums for answers. Do I need to install nautilus to get full previews? Seems like that may be the easiest way.

---

### Post by nerdtron on 2013-04-16
I installed nemo and nautilus, still no video thumbnails. Edit>Preferences>Preview changed to 4GB still no change. How about yours?

---

### Post by pqwoerituytrueiwoq on 2013-04-16
```
sudo apt-get install tumbler-plugins-extra
```
works here
[[IMG]http://www.zimagez.com/miniature/screenshot-04162013-101451pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-04162013-101451pm.php")
tested with the flash video here
[http://www.youtube.com/watch?v=QRlrl9dzp6E](http://www.youtube.com/watch?v=QRlrl9dzp6E)

running 13.04 here

---

### Post by nerdtron on 2013-04-16
Already installed that package along with tumbler. Still no good.
BTW what version of thunar is that?

---

### Post by pqwoerituytrueiwoq on 2013-04-17
```
Thunar 1.6.2 (Xfce 4.10)

Copyright (c) 2004-2012
    The Thunar development team. All rights reserved.

Written by Benedikt Meurer <benny (at) xfce.org>.

Please report bugs to <http://bugzilla.xfce.org/>.
```
stock on xubuntu 13.04
12.10 can get it with this ppa
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12)
12.04 will need that and this one
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

---

### Post by nerdtron on 2013-04-17
hhhmmmm same Thunar as mine, in Ubuntu 12.10. Did you have to edit any config files or run any service after installing tumbler?

---

### Post by pqwoerituytrueiwoq on 2013-04-17
nope, all i did was open synaptic and look up tumbler and read the description and installed it, that video is under 10MB, i am not sure what the size limit is (edit just checked 346.4MB and it still works)

here is a list of every package i have installed on xubuntu 13.04
```
bum php5-cli imagemagick xdotool cups-pdf openshot libavformat-extra-53 undistract-me medibuntu-keyring sqlite3 usermode ubuntu-sounds xul-ext-gdata-provider wakeonlan audio-recorder cowsay fortune ubuntu-wallpapers-lucid hddtemp hwinfo openssh-server gdebi dconf-tools easymp3gain-gtk gnome-system-log gnome-nettool soundconverter bleachbit kazam key-mon ubuntuone-control-panel-qt curl vorbis-tools ttf-mscorefonts-installer xfce4-genmon-plugin linux numlockx ubuntu-wallpapers-precise ubuntu-wallpapers-quantal ubuntu-wallpapers shimmer-wallpapers synaptic supertuxkart hedgewars libreoffice gnome-games geany geany-plugin-spellcheck geany-plugin-treebrowser gparted gufw smplayer vlc audacity tree gcolor2 rar p7zip-full chromium-browser gsmartcontrol gnome-disk-utility screenruler xfce4-diskperf-plugin tumbler-plugins-extra xbacklight xfce4-power-manager-plugins cameramonitor paprefs
```

this is everything i did to my sources
```
sudo sed -i 's/# deb h/deb h/' /etc/apt/sources.list
sudo apt-add-repository --yes ppa:xubuntu-dev/xfce-4.12
echo "deb http://archive.getdeb.net/ubuntu quantal-getdeb apps games" | sudo tee -a /etc/apt/sources.list
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
```

this is a list of everything i have purged
```
thunderbird-globalmenu firefox-globalmenu gnumeric gnumeric-common gnumeric-doc libgtkmathview0c2a libabiword-2.9 abiword-plugin-mathview abiword-plugin-grammar abiword-common abiword gir1.2-dee-1.0 gir1.2-unity-5.0 unity-chromium-extension
```

---

### Post by Sam Mills on 2013-04-23
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get install tumbler-plugins-extra
```
works here
[[IMG]http://www.zimagez.com/miniature/screenshot-04162013-101451pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-04162013-101451pm.php")
tested with the flash video here
[http://www.youtube.com/watch?v=QRlrl9dzp6E](http://www.youtube.com/watch?v=QRlrl9dzp6E)

running 13.04 here

Thanks, I had that before, but it didn't do anything. I just checked my videos again, and now it works! Go figure. Anyway, thanks for the help people.

---

