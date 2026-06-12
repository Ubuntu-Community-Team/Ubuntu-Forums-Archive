---
title: "installing Macromedia 7 plugin for Firefox on Ubuntu"
date: 2005-06-05
forum: General Help
---

### Post by Paul Panks on 2005-06-05
I tried both the manual install and the automated installation, but both failed to install Macromedia 7 Flash for Firefox.

Has anyone else experienced this problem? I'm unable to do anything on the desktop because I am not "root", and the only way I can (presumedly) be root is through sudo su in the xterm console window.

Paul

---

### Post by Seti on 2005-06-05
Just get the installer from Macromedia Flash 7, download it to your /home/user

then just ```
tar xvzf install_flash_player_7_linux.tar.gz
``` 
and then```
cd install_flash_player_7_linux
``` 
now ```
sudo ./flashplayer-installer
``` 
In fact, you may not even need to sudo it, just try running it with your own user acct.

---

### Post by Majlo on 2005-06-05
Or type in console :

*sudo apt-get install flashplayer-mozilla*

---

### Post by codejunkie on 2005-06-05
this might help you it makes it a little easier to access files thru nautilus as Root

just add a launcher to the desktop with the command: gksudo nautilus then in nautilus click edit preferences under the Behavior tab check Always open in browser windows restart nautilus then it will always open in browser mode like kde and windows file manager with this you'll have full root access to all files so you can just drag and drop files, change permissions etc, the easy way. so you can just copy and paste the flash plugin files into the /usr/lib/mozilla and /usr/lib/mozilla-firefox directories hope this helps.

---

### Post by az on 2005-06-05
Install 
flashplugin-nonfree

from Multiverse.  It downloads the latest flash for you and installs it.  It is easy to remove, too!

---

### Post by Seti on 2005-06-05
[QUOTE=codejunkie]this might help you it makes it a little easier to access files thru nautilus as Root

just add a launcher to the desktop with the command: gksudo nautilus then in nautilus click edit preferences under the Behavior tab check Always open in browser windows restart nautilus then it will always open in browser mode like kde and windows file manager with this you'll have full root access to all files so you can just drag and drop files, change permissions etc, the easy way. so you can just copy and paste the flash plugin files into the /usr/lib/mozilla and /usr/lib/mozilla-firefox directories hope this helps.[/QUOTE]

Running X as root? Pretty dangerous I'd say, good for the adventurous. This usually results in new users complaining that they can no longer use their system after they borked it good deleting and moving stuff as root. just my 2 cents.

---

### Post by codejunkie on 2005-06-06
[QUOTE=Seti]Running X as root? Pretty dangerous I'd say, good for the adventurous. This usually results in new users complaining that they can no longer use their system after they borked it good deleting and moving stuff as root. just my 2 cents.[/QUOTE]

yes you could do some damage if you don't know what your doing but you can do just as much thru the terminal if you don't know what your doing :) this is just an easier way for new users to adjust that have never used gnome and are used to kde and windows file manager.

---

