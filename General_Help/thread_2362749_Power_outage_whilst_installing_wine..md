---
title: "Power outage whilst installing wine."
date: 2017-06-01
forum: General Help
---

### Post by makem2 on 2017-06-01
I was installing wine and ubuntu software centre hangs when trying to continue the install. The folder ~/.wine is missing and ubuntu software centre says wine is installed but hangs when uninstalling it.

I had installed a 64 bit working version of wine and winetricks, then found I needed a 32 bit version.

```

makem@ssdTOSH:/$ sudo winecfg
wine: '/home/makem' is not owned by you, refusing to create a configuration directory there
makem@ssdTOSH:/$

```

Tried:
```

[COLOR=#000000][FONT=verdana]rm -r ~/.local/share/applications/wine[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]rm ~/.local/share/applications/wine*
[/FONT][/COLOR]
```

When I search for 'wine' I find there are 280 files still remaining.

How can I clean up everything and start from scratch?

---

### Post by #&amp;thj^% on 2017-06-01
Sorry I'm a bit confused by "Power outage" in your title.
Try seeing if indeed it is installed
```
apt policy wine winetricks
```

---

### Post by makem2 on 2017-06-01
Thanks for you quick reply. Power outage = electricity supply failed.

```

makem@ssdTOSH:~$ apt policy wine winetricks
wine:
  Installed: 1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1
  Candidate: 1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1
  Version table:
 *** 1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1 500
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     1:1.6.2-0ubuntu14 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
winetricks:
  Installed: 0.0+20141009+svn1208-2ubuntu1
  Candidate: 0.0+20141009+svn1208-2ubuntu1
  Version table:
 *** 0.0+20141009+svn1208-2ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
        100 /var/lib/dpkg/status
makem@ssdTOSH:~$

```

---

### Post by #&amp;thj^% on 2017-06-01
Ok Thanks! ;) Strange I find this:
> !!! PLEASE NOTE THAT THIS REPOSITORY IS DEPRECATED !!!

In fact, it's double deprecated -- it was replaced by the Wine Builds PPA, which was then itself replaced.

For more information, please see:

    [https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html](https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html)

The following commands can be used to add the new repository:

    wget [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)
    sudo apt-key add Release.key
    sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'
**But lets see if we can sort this before adding more PPA's**
Paste back the contents from the terminal:
```
inxi -r 
```

---

### Post by makem2 on 2017-06-01
```

makem@ssdTOSH:~$ inxi -r
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial restricted main
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial restricted main
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates restricted main
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates restricted main
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial universe
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial universe
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial-backports restricted universe multiverse main
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-backports restricted universe multiverse main
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security restricted main
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-security restricted main
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security universe
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-security universe
           deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security multiverse
           deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-security multiverse
           deb-src http://archive.canonical.com/ubuntu trusty partner
           deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main
           Active apt sources in file: /etc/apt/sources.list.d/cinelerra-ppa-ubuntu-ppa-xenial.list
           deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial main
           Active apt sources in file: /etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-xenial.list
           deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial main
           Active apt sources in file: /etc/apt/sources.list.d/google-chrome.list
           deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
           Active apt sources in file: /etc/apt/sources.list.d/google-earth.list
           deb http://dl.google.com/linux/earth/deb/ stable main
           Active apt sources in file: /etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list
           deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial main
           Active apt sources in file: /etc/apt/sources.list.d/qbittorrent-team-ubuntu-qbittorrent-stable-xenial.list
           deb http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial main
           Active apt sources in file: /etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list
           deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
           Active apt sources in file: /etc/apt/sources.list.d/xenial-partner.list
           deb http://archive.canonical.com/ubuntu xenial partner #Added by software-center
makem@ssdTOSH:~$

```

---

### Post by #&amp;thj^% on 2017-06-01
Sorry had a customer to deal with.
Ok this is the offending Repo:
"http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main"
Which is the Quote I posted earlier as 
> !!! PLEASE NOTE THAT THIS REPOSITORY IS DEPRECATED !!!
So you would need to purge or remove that one.
I see that you do have the correct one already: "deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main"

Now after removing the bad PPA you can update your sources again.
Now if you want a clean install to start fresh with wine:
```
sudo apt remove --purge wine winetricks
sudo apt -f autoremove
```
Then try your install again, and maybe try the terminal with your install this time.:D

---

### Post by makem2 on 2017-06-01
```

makem@ssdTOSH:~$ sudo apt remove --purge wine winetricks
[sudo] password for makem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  p7zip
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED
  wine* winetricks*
0 to upgrade, 0 to newly install, 2 to remove and 16 not to upgrade.
2 not fully installed or removed.
After this operation, 798 kB disk space will be freed.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 253994 files and directories currently installed.)
Removing wine (1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1) ...
Removing winetricks (0.0+20141009+svn1208-2ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libsasl2-modules:i386:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.


dpkg: error processing package libsasl2-modules:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Errors were encountered while processing:
 libssl1.0.0:i386
 libsasl2-modules:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
makem@ssdTOSH:~$ sudo apt -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  p7zip
0 to upgrade, 0 to newly install, 1 to remove and 16 not to upgrade.
2 not fully installed or removed.
After this operation, 1,000 kB disk space will be freed.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 253985 files and directories currently installed.)
Removing p7zip (9.20.1~dfsg.1-4.2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libsasl2-modules:i386:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.


dpkg: error processing package libsasl2-modules:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Errors were encountered while processing:
 libssl1.0.0:i386
 libsasl2-modules:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
makem@ssdTOSH:~$ 
makem@ssdTOSH:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 16 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libsasl2-modules:i386:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.


dpkg: error processing package libsasl2-modules:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Errors were encountered while processing:
 libssl1.0.0:i386
 libsasl2-modules:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
makem@ssdTOSH:~$

```

Lots of errors. Is it safe to continue?

EDIT:
```

makem@ssdTOSH:~$ sudo ppa-purge [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial main
Updating packages lists
PPA to be removed: [http://ppa.launchpad.net/ubuntu-wine/ppa](http://ppa.launchpad.net/ubuntu-wine/ppa) ubuntu
Warning:  Could not find package list for PPA: 
[http://ppa.launchpad.net/ubuntu-wine/ppa](http://ppa.launchpad.net/ubuntu-wine/ppa) ubuntu
makem@ssdTOSH:~$ sudo ppa-purge "http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main"
Updating packages lists
PPA to be removed: [http://ppa.launchpad.net/ubuntu-wine/ppa](http://ppa.launchpad.net/ubuntu-wine/ppa) ubuntu xenial main
Warning:  Could not find package list for PPA: 
[http://ppa.launchpad.net/ubuntu-wine/ppa](http://ppa.launchpad.net/ubuntu-wine/ppa) ubuntu xenial main
makem@ssdTOSH:~$

```

I had un-checked it in software & updates.

---

### Post by #&amp;thj^% on 2017-06-01
> **makem2 said:**
> ```

makem@ssdTOSH:~$ sudo apt remove --purge wine winetricks
[sudo] password for makem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  p7zip
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED
  wine* winetricks*
0 to upgrade, 0 to newly install, 2 to remove and 16 not to upgrade.
2 not fully installed or removed.
After this operation, 798 kB disk space will be freed.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 253994 files and directories currently installed.)
Removing wine (1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1) ...
Removing winetricks (0.0+20141009+svn1208-2ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libsasl2-modules:i386:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.


dpkg: error processing package libsasl2-modules:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Errors were encountered while processing:
 libssl1.0.0:i386
 libsasl2-modules:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
makem@ssdTOSH:~$ sudo apt -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  p7zip
0 to upgrade, 0 to newly install, 1 to remove and 16 not to upgrade.
2 not fully installed or removed.
After this operation, 1,000 kB disk space will be freed.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 253985 files and directories currently installed.)
Removing p7zip (9.20.1~dfsg.1-4.2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libsasl2-modules:i386:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.


dpkg: error processing package libsasl2-modules:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Errors were encountered while processing:
 libssl1.0.0:i386
 libsasl2-modules:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
makem@ssdTOSH:~$ 
makem@ssdTOSH:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 16 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libsasl2-modules:i386:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.


dpkg: error processing package libsasl2-modules:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Errors were encountered while processing:
 libssl1.0.0:i386
 libsasl2-modules:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
makem@ssdTOSH:~$

```

Lots of errors. Is it safe to continue?

EDIT:
```

makem@ssdTOSH:~$ sudo ppa-purge [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial main
Updating packages lists
PPA to be removed: [http://ppa.launchpad.net/ubuntu-wine/ppa](http://ppa.launchpad.net/ubuntu-wine/ppa) ubuntu
Warning:  Could not find package list for PPA: 
[http://ppa.launchpad.net/ubuntu-wine/ppa](http://ppa.launchpad.net/ubuntu-wine/ppa) ubuntu
makem@ssdTOSH:~$ sudo ppa-purge "http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main"
Updating packages lists
PPA to be removed: [http://ppa.launchpad.net/ubuntu-wine/ppa](http://ppa.launchpad.net/ubuntu-wine/ppa) ubuntu xenial main
Warning:  Could not find package list for PPA: 
[http://ppa.launchpad.net/ubuntu-wine/ppa](http://ppa.launchpad.net/ubuntu-wine/ppa) ubuntu xenial main
makem@ssdTOSH:~$

```

I had un-checked it in software & updates.

Humm? I'm not sure how you added it in the first place, all I get is 404 not found???
But give this a shot:
```
sudo ppa-purge ppa:ubuntu-wine/ppa
```
If needed post back the results so we can maybe figure this one out. :)

---

### Post by makem2 on 2017-06-01
```

makem@ssdTOSH:~$ sudo ppa-purge ppa:ubuntu-wine/ppa
[sudo] password for makem: 
Updating packages lists
PPA to be removed: ubuntu-wine ppa
Warning:  Could not find package list for PPA: ubuntu-wine ppa
makem@ssdTOSH:~$ 

```

I tried to open synaptic but it failed so:

```

makem@ssdTOSH:~$ sudo dpkg --configure -a
[sudo] password for makem: 
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
Setting up fonts-unfonts-core (1.0.3.is.1.0.2-080608-10ubuntu1) ...
Setting up fonts-horai-umefont (590-1) ...
Setting up libsasl2-modules:i386 (2.1.26.dfsg1-14build1) ...
Setting up libexif12:i386 (0.6.21-2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link
makem@ssdTOSH:~$ sudo apt-get clean
makem@ssdTOSH:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
makem@ssdTOSH:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  fonts-horai-umefont fonts-unfonts-core libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libcapi20-3 libcapi20-3:i386
  libexif12:i386 libgd3:i386 libgif7:i386 libglu1-mesa:i386 libgphoto2-6:i386 libgphoto2-port12:i386 libgssapi3-heimdal:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libieee1284-3:i386 libjack-jackd2-0:i386
  libkrb5-26-heimdal:i386 libldap-2.4-2:i386 libltdl7:i386 libmpg123-0:i386 libodbc1 libopenal1:i386 libosmesa6 libosmesa6:i386
  libp11-kit-gnome-keyring:i386 libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libspeexdsp1:i386 libssl1.0.0:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386 libvpx3:i386
  libwind0-heimdal:i386 libxpm4:i386 ocl-icd-libopencl1:i386 odbcinst odbcinst1debian2 p11-kit-modules:i386 unixodbc wine1.6 wine1.6-amd64
  wine1.6-i386:i386
0 to upgrade, 0 to newly install, 51 to remove and 16 not to upgrade.
After this operation, 402 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 253916 files and directories currently installed.)
Removing fonts-horai-umefont (590-1) ...
Removing fonts-unfonts-core (1.0.3.is.1.0.2-080608-10ubuntu1) ...
Removing libasound2-plugins:i386 (1.1.0-0ubuntu1) ...
Removing libcapi20-3:i386 (1:3.27-1) ...
Removing libcapi20-3:amd64 (1:3.27-1) ...
Removing libsane:i386 (1.0.25+git20150528-1ubuntu2.16.04.1) ...
Removing libgif7:i386 (5.1.4-0.3~16.04) ...
Removing libieee1284-3:i386 (0.2.11-12) ...
Removing libjack-jackd2-0:i386 (1.9.10+20150825git1ed50c92~dfsg-1ubuntu1) ...
Removing unixodbc (2.3.1-4.1) ...
Removing libodbc1:amd64 (2.3.1-4.1) ...
Removing libosmesa6:i386 (12.0.6-0ubuntu0.16.04.1) ...
Removing libosmesa6:amd64 (12.0.6-0ubuntu0.16.04.1) ...
Removing libp11-kit-gnome-keyring:i386 (3.18.3-0ubuntu2) ...
Removing libsamplerate0:i386 (0.1.8-8) ...
Removing libsasl2-modules:i386 (2.1.26.dfsg1-14build1) ...
Removing libspeexdsp1:i386 (1.2~rc1.2-1ubuntu1) ...
Removing libssl1.0.0:i386 (1.0.2g-1ubuntu4.6) ...
Removing libv4l-0:i386 (1.10.0-1) ...
Removing libv4lconvert0:i386 (1.10.0-1) ...
Removing p11-kit-modules:i386 (0.23.2-5~ubuntu16.04.1) ...
Removing odbcinst (2.3.1-4.1) ...
Removing odbcinst1debian2:amd64 (2.3.1-4.1) ...
Removing wine1.6 (1:1.6.2-0ubuntu14) ...
Removing wine1.6-amd64 (1:1.6.2-0ubuntu14) ...
Removing wine1.6-i386:i386 (1:1.6.2-0ubuntu14) ...
Removing libldap-2.4-2:i386 (2.4.42+dfsg-2ubuntu3.2) ...
Removing libgssapi3-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libheimntlm0-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libkrb5-26-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libhx509-5-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libasound2:i386 (1.1.0-0ubuntu1) ...
Removing libgphoto2-6:i386 (2.5.9-3) ...
Removing libexif12:i386 (0.6.21-2) ...
Removing libgd3:i386 (2.1.1-4ubuntu0.16.04.6) ...
Removing libglu1-mesa:i386 (9.0.0-2.1) ...
Removing libgphoto2-port12:i386 (2.5.9-3) ...
Removing libhcrypto4-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libheimbase1-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libltdl7:i386 (2.4.6-0.1) ...
Removing libmpg123-0:i386 (1.22.4-1) ...
Removing libopenal1:i386 (1:1.16.0-3) ...
Removing libwind0-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libsasl2-2:i386 (2.1.26.dfsg1-14build1) ...
Removing libsasl2-modules-db:i386 (2.1.26.dfsg1-14build1) ...
Removing libusb-1.0-0:i386 (2:1.0.20-1) ...
Removing libvpx3:i386 (1.5.0-2ubuntu1) ...
Removing libxpm4:i386 (1:3.5.11-1ubuntu0.16.04.1) ...
Removing ocl-icd-libopencl1:i386 (2.2.8-1) ...
Removing libasn1-8-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Removing libroken18-heimdal:i386 (1.7~git20150920+dfsg-4ubuntu1) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
makem@ssdTOSH:~$ sudo apt-get update
Hit:1 https://dl.winehq.org/wine-builds/ubuntu xenial InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                                                           
Ign:3 http://archive.canonical.com/ubuntu trusty InRelease                                
Hit:4 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial InRelease                                            
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                              
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                          
Hit:7 http://archive.canonical.com/ubuntu xenial InRelease                                          
Hit:8 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease                  
Ign:9 http://dl.google.com/linux/earth/deb stable InRelease                                          
Get:10 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                                                  
Get:11 http://gb.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                  
Hit:12 http://archive.canonical.com/ubuntu trusty Release                                                                       
Hit:14 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease
Hit:15 http://dl.google.com/linux/chrome/deb stable Release
Hit:17 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial InRelease                                                        
Hit:18 http://dl.google.com/linux/earth/deb stable Release                                                                                         
Fetched 306 kB in 8s (37.4 kB/s)                                                                                                                   
Reading package lists... Done
makem@ssdTOSH:~$ sudo ppa-purge ppa:ubuntu-wine/ppa
Updating packages lists
PPA to be removed: ubuntu-wine ppa
Warning:  Could not find package list for PPA: ubuntu-wine ppa
makem@ssdTOSH:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 16 not to upgrade.
makem@ssdTOSH:~$ 

```

No errors in auto remove now - safe to reinstall wine?

---

### Post by #&amp;thj^% on 2017-06-01
Sure...Go for it.:)
EDIT: BTW the only package I ever install for wine is "**winetricks**"
That will put a hidden .wine folder inside your home directory.

---

### Post by makem2 on 2017-06-02
> **1fallen said:**
> Sure...Go for it.:)
EDIT: BTW the only package I ever install for wine is "**winetricks**"
That will put a hidden .wine folder inside your home directory.

You don't follow:

[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

Then install winetricks?

I thought installing wine put the hidden .wine folder and that winetricks was necessary later.

EDIT: I see, you install wine then use the winetricks package to install whatever is needed. I did think it was the install of wine which made the.wine folder but I will check this time.

Thank you for your assistance.

---

### Post by makem2 on 2017-06-02
Yes, it is necessary to run winetricks to make the .wine folder after first installing wine. :p

---

