---
title: "Can anyone post a script undoing all of this source installation?"
date: 2007-01-14
forum: General Help
---

### Post by darweth on 2007-01-14
I would like to undo this entire script for various reasons.  Uninstall MPlayer and MPlayer-Plugin.  Can anyone help?  Thanks. :)  Posting a script i can run (.sh) would be much appreciated. :)

```
#!/bin/bash
if [ `id -u` != "0" ]; then
	echo "You should be root to run this script."
	exit 1
fi
apt-get install build-essential libpng12-dev libpng3-dev libgtk1.2-dev libgtkgl2.0-dev libgtkmm2.0-dev libgtk2.0-dev libwxgtk2.4-dev libx11-dev libxpm-dev libxt-dev firefox-dev
cd
mkdir mplayer-temp
cd mplayer-temp
wget http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc1.tar.bz2
wget http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20061022.tar.bz2
wget http://www.mplayerhq.hu/MPlayer/skins/clearplayer-0.8.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.31.tar.gz
tar -xf MPlayer-1.0rc1.tar.bz2
tar -xf essential-20061022.tar.bz2
tar -xf clearplayer-0.8.tar.bz2
tar -xf mplayerplug-in-3.31.tar.gz
mkdir /usr/local/share/mplayer/
ln -s /usr/share/fonts/truetype/freefont/FreeSans.ttf /usr/local/share/mplayer/subfont.ttf
mkdir /usr/local/share/mplayer/skins/
cp --recursive clearplayer/ /usr/local/share/mplayer/skins/
ln -s /usr/local/share/mplayer/skins/clearplayer/ /usr/local/share/mplayer/skins/default
mkdir /usr/local/lib/codecs/
cp essential-20061022/* /usr/local/lib/codecs/
cd MPlayer-1.0rc1
./configure --enable-gui
make -s
make install
cd ../mplayerplug-in
./configure
make -s
cp mplayerplug-in*.so /usr/lib/firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/firefox/components
cd
rm -rf mplayer-temp
```

---

### Post by david_2001 on 2007-01-14
Firstly, you could try asking the author - I've seen this script elsewhere in these forums.  Otherwise, it shouldn't be too difficult to undo but would have been easier if the original script hadn't deleted the source directories.  Leaving them intact would have allowed a "make uninstall" to do most of the work!  Anyway, I'm not going to write a script but it isn't too difficult to do manually.

Let's assume that most of the install was in /usr/local.  You can confirm this by checking where the mplayer binary is located.  Enter the following at a console prompt:
```
which mplayer
```
It should be in /usr/local/bin.  In which case, the first steps are going to be:
```
sudo rm /usr/local/bin/mplayer
sudo rm /usr/local/bin/gmplayer

```
If the mplayer binary is in /usr/local/bin then the mplayer libraries are going to be in /usr/local/lib.  Confirm this by trying to list the directory:
```
ls /usr/local/lib/mplayer
```
If you get something like (it could be different):
> $ ls /usr/local/lib/mplayer/
vidix and not "No such file or directory" then you have a result.  Enter the following:
```
sudo rm -rf /usr/local/lib/mplayer
```
Mplayer also creates stuff in the share directory.  It should be in /usr/local/share, so confirm and delete:
```
ls /usr/local/share/mplayer
```
If you get a result then enter:
```
sudo rm -rf /usr/local/share/mplayer
```
That should be most of it gone!  Now to tidy up:
```
sudo rm /usr/lib/firefox/plugins/mplayerplug-in*.so
sudo rm /usr/lib/firefox/components/mplayerplug-in*.xpt
sudo rm -rf /usr/local/lib/codecs
sudo rm -rf /usr/local/etc/mplayer
sudo rm -rf /etc/mplayer
rm -rf .mplayer
```
If you want to get rid of the various additional packages that were installed then enter:
```
apt-get --purge remove build-essential libpng12-dev libpng3-dev libgtk1.2-dev libgtkgl2.0-dev libgtkmm2.0-dev libgtk2.0-dev libwxgtk2.4-dev libx11-dev libxpm-dev libxt-dev firefox-dev

```

Job done.  There will still be some bits and pieces left over, such as user documentation and localisations but they won't do any harm and can be safely left to lurk wherever they are lurking.

---

### Post by david_2001 on 2007-01-14
A couple of quality control moments:

/usr/local/bin/mencoder will also need deleting.

The "apt-get --purge ..." command needs to start with "sudo"

---

