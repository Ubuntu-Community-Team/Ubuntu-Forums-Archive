---
title: "Ubuntu 12.04 64bit DVD playback in previously Medibuntu installed system"
date: 2013-10-21
forum: General Help
---

### Post by psfal on 2013-10-21
[COLOR=#000000][FONT=Calibri] In new installs, it's no issue to install DVD playback support. But in older installs where Medibuntu was used I get this when I try to enable DVD support.[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]I use the following:[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]sudo apt-[COLOR=#0000FF][FONT=inherit]get[/FONT][/COLOR] install ubuntu-restricted-extras
sudo apt-[COLOR=#0000FF][FONT=inherit]get[/FONT][/COLOR] install libavformat-extra-53 libavcodec-extra-53 libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
sudo apt-[COLOR=#0000FF][FONT=inherit]get[/FONT][/COLOR] install vlc[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]I was wondering if you have a fix for this? Here's the output I get...

cipher@cipher-ThinkPad-R61e:~$ sudo apt-get install libavformat-extra-53 libavcodec-extra-53 libdvdread4
[sudo] password for cipher: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
libavcodec-extra-53 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libavformat-extra-53 : Depends: libavcodec-extra-53 (< 4:0.8.6ubuntu0.12.04.1-99) but 4:0.8.6ubuntu0.12.04.1+medibuntu1 is to be installed
                        Depends: libavutil-extra-51 (< 4:0.8.6ubuntu0.12.04.1-99) but 4:0.8.6ubuntu0.12.04.1+medibuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
cipher@cipher-ThinkPad-R61e:~$ sudo apt-get -f install libavformat-extra-53 libavcodec-extra-53 libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
libavcodec-extra-53 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libavformat-extra-53 : Depends: libavcodec-extra-53 (< 4:0.8.6ubuntu0.12.04.1-99) but 4:0.8.6ubuntu0.12.04.1+medibuntu1 is to be installed
                        Depends: libavutil-extra-51 (< 4:0.8.6ubuntu0.12.04.1-99) but 4:0.8.6ubuntu0.12.04.1+medibuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.



I've done all that I know to do to repair or remove broken packages. Any suggestions? How do I remove all Medibuntu references from the system to avoid these errors?
[/FONT][/COLOR]

---

### Post by philinux on 2013-10-21
Go into your software sources and remove the medibuntu repos. Then update the system.

The install.sh script has now been updated and released to older releases to not point to medibuntu but videolan instead. No repo required now.

---

### Post by psfal on 2013-10-25
> **philinux said:**
> Go into your software sources and remove the medibuntu repos. Then update the system.

The install.sh script has now been updated and released to older releases to not point to medibuntu but videolan instead. No repo required now.

I had already removed the Medibuntu repository. The error still showed up afterwards, I wound up doing a fresh install and the problem is gone. Thanks so much for your help :D

---

