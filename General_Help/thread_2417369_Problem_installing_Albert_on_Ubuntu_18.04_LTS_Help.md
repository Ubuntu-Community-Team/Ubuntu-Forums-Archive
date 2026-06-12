---
title: "Problem installing Albert on Ubuntu 18.04 LTS Help?!?"
date: 2019-04-22
forum: General Help
---

### Post by jebi on 2019-04-22
hi

cant install albert doing this...

sudo add-apt-repository ppa:nilarimogard/webupd8

gets..

 The main Web Upd8 PPA maintained by: [http://www.webupd8.org/](http://www.webupd8.org/)


To add this PPA, simply paste this in a terminal:
sudo add-apt-repository ppa:nilarimogard/webupd8


Packages in this PPA: audacious, ap-hotspot, awn-applet-radio, awn-applet-wm, calise, cmus, dockbarx, dockbarx-themes-extra, dropbox-share, emerald, exaile, fbmessenger, gnome-subtitles, gnome-window-applets, grsync, grive, gthumb, launchpad-getkeys, mc, mdm (Mint Display Manager), minitunes, minitube, musique, notifyosdconfig, nautilus-columns, powertop, ppa-purge, rosa-media-player, fixed pulseaudio-equalizer, subtitleeditor, syncwall, umplayer, unity-reboot, wimlib, youtube-dl, xfce4-dockbarx-plugin, xournal, yad, yarock and others. Almost all packages are updated to their latest version.


For other (specialized) PPAs we maintain, see: [https://launchpad.net/~webupd8team](https://launchpad.net/~webupd8team)
 More info: [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

press enter

Ign:1 [http://download.opensuse.org/repositories/home:/manuelschneid3r/xUbuntu_17.10](http://download.opensuse.org/repositories/home:/manuelschneid3r/xUbuntu_17.10) bionic InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Hit:3 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) bionic InRelease    
Err:4 [http://download.opensuse.org/repositories/home:/manuelschneid3r/xUbuntu_17.10](http://download.opensuse.org/repositories/home:/manuelschneid3r/xUbuntu_17.10) bionic Release
  404  Not Found [IP: 195.135.221.134 80]
Ign:5 [http://ppa.launchpad.net/synapse-core/ppa/ubuntu](http://ppa.launchpad.net/synapse-core/ppa/ubuntu) bionic InRelease        
Ign:6 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable InRelease                      
Hit:7 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release                        
Err:9 [http://ppa.launchpad.net/synapse-core/ppa/ubuntu](http://ppa.launchpad.net/synapse-core/ppa/ubuntu) bionic Release          
  404  Not Found [IP: 91.189.95.83 80]
Get:10 [http://mirror.linux.pizza/ubuntu](http://mirror.linux.pizza/ubuntu) bionic InRelease [242 kB]
Get:11 [http://mirror.linux.pizza/ubuntu](http://mirror.linux.pizza/ubuntu) bionic-updates InRelease [88.7 kB]     
Get:12 [http://mirror.linux.pizza/ubuntu](http://mirror.linux.pizza/ubuntu) bionic-backports InRelease [74.6 kB]   
Get:13 [http://mirror.linux.pizza/ubuntu](http://mirror.linux.pizza/ubuntu) bionic-security InRelease [88.7 kB]    
Reading package lists... Done                                                  
E: The repository 'http://download.opensuse.org/repositories/home:/manuelschneid3r/xUbuntu_17.10 bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/synapse-core/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

error?

then


sudo apt-get update
sudo apt-get install albert

gets..
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package albert

what am i doing wrong?

thx

---

