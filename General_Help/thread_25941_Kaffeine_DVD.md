---
title: "Kaffeine DVD ?"
date: 2005-04-11
forum: General Help
---

### Post by ThePainter on 2005-04-11
Hi,
Ive just upgraded my Warty to Hoary.
All went Ok exept synaptic disappeared and I had to install it via apt-get ?

Any way I always ran Kaffeine as my only Media player but when I loaded the updated one it did the usual chack and came back with "No /dev/dvd" and when I try to open or play a dvd I jsut get a list of errors saying cant read, no disc in drive etc.
Im Warty we had to put a symlink in for dvd but there isnt any mension in the hoary guide and the old warty fix file line doesnt match the new one.
They mount on the desktop and can open in nautilus but wont play as DVD or vob ?

I have done a search but nothing turned up concerning this problem ?

Any ideas how to get dvd's to play ?

---

### Post by segrewb on 2005-04-11
Look at this thread [here](http://www.ubuntuforums.org/showthread.php?t=23646&highlight=%2Fdev%2Fdvd) .

Hope it helps.

---

### Post by segrewb on 2005-04-11
This is the section of the thread I'm talking about.  Should work for Kaffeine also.

Originally Posted by clb137
HI, 

Have looked at the guide [http://ubuntuguide.org/](http://ubuntuguide.org/) for 'warty' and [http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/) for 'hoary' 

You need to download and configure as follows but the guide tells you all

1. add extra repositires

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

2. Install codecs

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs

3. DVD playback capability

sudo apt-get install libdvdcss2

4. Install xine-ui

sudo apt-get install xine-ui

5. Symbolic link

sudo ln -sf /dev/cdrom /dev/dvd
sudo cp /etc/udev/udev.rules /etc/udev/udev.rules_backup
sudo gedit /etc/udev/udev.rules

add the following line

# /dev/cdrom symlink
BUS="ide", KERNEL="hd[a-z]", SYMLINK="cdrom dvd"

(see the following sample file) [http://ubuntuguide.org/sample/udev.rules_symbolicdevdvd](http://ubuntuguide.org/sample/udev.rules_symbolicdevdvd)

good luck

clinton

---

### Post by ThePainter on 2005-04-11
Hi,
Thanks  :grin:

---

