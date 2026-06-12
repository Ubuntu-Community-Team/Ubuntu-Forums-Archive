---
title: "Please help! Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-08-23
forum: General Help
---

### Post by sam79 on 2014-08-23
I'm fairly new to Ubuntu. I was having some difficulties with Lindvd a few weeks ago so I tried to uninstall it. Something went wrong and now I can't install anything. 

This is what I get when I run apt-get install -f

```
sam@dell-desktop:~$ sudo apt-get install -f
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  compiz-plugins-extra compiz-plugins-main famfamfam-flag-png fonts-uralic
  gnome-dictionary gnome-search-tool gwibber-service libftgl2 libgdict-1.0-6
  libgdict-common libircclient1 liblua5.1-0 libreoffice-voikko
  libreoffice-writer2latex libxerces-c3.1 megaglest megaglest-data
  printer-driver-hpijs
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  poppler-data
The following packages will be REMOVED:
  lindvd
The following NEW packages will be installed:
  poppler-data
0 upgraded, 1 newly installed, 1 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,479 kB of archives.
After this operation, 3,567 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 490379 files and directories currently installed.)
Removing lindvd (1.2.5.34.dell-ubuntu1) ...
dpkg: error processing package lindvd (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 lindvd
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Bashing-om on 2014-08-23
sam79; Hi ! Welcome to the forum .


What release are you running ?
I looked in the 14.04 software repository and there is no "lindvd" application available,
> 
sysop@1404mini:~$ apt-cache show lindvd
N: Unable to locate package lindvd
E: No packages found
sysop@1404mini:~$ 


If you installed "lindvd" from 3rd party sources, then ubuntu's package manager can not track it; 'apt-get' can not work with it. There should be directions either in the code you uncompressed, or on the web site to uninstall the application.

So, how did you install "lindvd" ?

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by sam79 on 2014-08-24
I think I installed it a while ago before I updated just using the package manager. It's a media player. It stopped working recently so I tried to uninstall it via the package manager, but it didn't work. Now I can't install anything. I've tried looking up similar problems, but I'm at a loss.

Every time I try to uninstall it, I get an error exit status 1. Lindvd shows up highlighted in red as a broken package in the package manager.

---

### Post by Bashing-om on 2014-08-24
sam79; Hey;

A quick search by uncle Google reveals that 'lindvd' is proprietary software.

Off the top of my head I do not know what it will take to remove the application. 
I will do a bit of research and see what I can come up with.


[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by sam79 on 2014-08-25
Let me just say right now that I have no idea what I'm doing. My brother in law installed Ubuntu onto a notebook he got me for Christmas some time ago. I want to say Lindvd was installed from the very beginning.

---

### Post by westie457 on 2014-08-25
Maybe this link will help. [http://wiki.ubuntuusers.de/LinDVD](http://wiki.ubuntuusers.de/LinDVD)

It is in German. The relevant part is 

**Deinstallation**

Um das Programm zu entfernen sind folgende Schritte notwendig [SUP][[2]]("http://wiki.ubuntuusers.de/LinDVD#source-2")[/SUP]:
```

sudo rm -dr /opt/LinDVD/                     #löscht den Ordner sowie dessen Inhalt
sudo rm /usr/local/bin/lindvd                #löscht den Link
sudo rm /usr/lib/libiviXXXX.so               #löscht die Lizenz
sudo rm /usr/share/pixmaps/LinDVD.xpm        #löscht das Icon
sudo ldconfig                                #neu einlesen der Biblitohekspfade 

```


Edit: to see the text here use the mouse to highlight -fixed

---

### Post by Bashing-om on 2014-08-25
@ sam79 Not a problem;

I had assumed such that someone else had installed the operating system. Yeah, 'lindvd'  did come pre-installed in some instances, from what Google reveals. westie457's find looks great to me as the means to remove it.

@ westie457 - To the rescue; again !

Remove these we know about and then see if the system reports any other instances of component files for 'lindvd' :
```

sudo find / -name "*lindvd*"

``` Might be something hiding about, maybe like in the /home directory.,

Then we check and make sure the package manager is in a happy state.,

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

