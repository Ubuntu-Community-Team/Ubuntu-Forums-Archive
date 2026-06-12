---
title: "broken package libsdl2"
date: 2014-12-26
forum: General Help
---

### Post by Ozzmosis88 on 2014-12-26
Hello!

Normally I dont ask for help as I can usually find answers to my problems, but this one has me running in circles...

I'm trying to install the new version of XBMC(Kodi). First thing was to upgrade Ubuntu to 14.04 as the previous version (13.10) is not supported, and I figured it was time to upgrade.

Everything on my system was running well and configured properly, so instead of performing a clean install of 14.04, I upgraded via software updater.

I had to clean up some obsolete packages in the system, and remove some apps etc etc, but eventually upgraded the system. Everything went fine escept I had a black screen after the initial reboot. I dropped to terminal and manually installed the latest Nvidia display drivers. Restarted LightDM, and all is well. Everything seems to work.

I found out that I lost PLEX, and XBMC was a mess. I reinstalled PLEX without issue, and removed XBMC and confirmed that I had the correct PPA, and tried to install Kodi, but failed with dependency issues. made sure to check for updates and applied a couple as required... Same result! 

[COLOR=#000000]```
 sudo apt-get install kodi 
```

[/COLOR]```
cory@CJS-XBMC:~$ sudo apt-get install kodi
[sudo] password for cory: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:


The following packages have unmet dependencies:
 kodi : Depends: kodi-bin (>= 2:14.0~git20141223.1015-final-0trusty) but it is not going to be installed
        Depends: kodi-bin (< 2:14.0~git20141223.1015-final-0trusty.1~) but it is not going to be installed

E: Unable to correct problems, you have held broken packages.
```[COLOR=#000000]

[/COLOR]OK So I add kodi-bin:

```
 sudo apt-get install kodi kodi-bin 
```

```
 cory@CJS-XBMC:~$ sudo apt-get install kodi kodi-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:


The following packages have unmet dependencies:
 kodi-bin : Depends: libsdl2-2.0-0 (>= 2.0.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages. 
```

I tried:
```
 cory@CJS-XBMC:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```[COLOR=#000000][FONT=Ubuntu Mono]

Contents of /etc/apt/sources.list:

[/FONT][/COLOR]```
 
# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty universe
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://ca.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-security universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-security multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main 
```

Tried this to look for held packages:
```
 cory@CJS-XBMC:~$ dpkg --get-selections | grep hold
cory@CJS-XBMC:~$ 
```

Nothing!

Now I'm not sure what to do. Ive searched for libsdl2-2.0-0 in Synaptic Package Manager, but it shows a red ! when marking to install, so I tried to repair the broken package...

[ATTACH=CONFIG]258804[/ATTACH]

Anyone have any ideas?

Thanks!

---

### Post by schragge on 2014-12-26
I'm tempted to suggest something like
```

sudo apt-get -f install libsdl2-2.0-0

```
Even if it fails, the output may contain clues as to why it cannot be installed.

Besides, let's see what packages are not in the cleanly installed state:
```

dpkg -l|sed -nr '/^.[^in]/s/^(.{78}).*/\1/p'

```

---

### Post by Ozzmosis88 on 2014-12-26
> **schragge said:**
> I'm tempted to suggest something like
```

sudo apt-get -f install libsdl2-2.0-0

```
Even if it fails, the output may contain clues as to why it cannot be installed.

Besides, let's see what packages are not in the cleanly installed state:
```

dpkg -l|sed -nr '/^.[^in]/s/^(.{78}).*/\1/p'

```

OK! Thanks for the reply! Here is the results:

```
 
cory@CJS-XBMC:~$ sudo apt-get -f install libsdl2-2.0-0
[sudo] password for cory: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:


The following packages have unmet dependencies:
 libsdl2-2.0-0 : Depends: libwayland-egl1-mesa (>= 10.0.2) but it is not going to be installed or
                          libwayland-egl1
E: Unable to correct problems, you have held broken packages.
cory@CJS-XBMC:~$

```

I searched libwayland-egl1-mesa and found it is part of the edgers/ppa which caused some grief during the upgrade from 13.10 -> 14.04

```

cory@CJS-XBMC:~$ dpkg -l|sed -nr '/^.[^in]/s/^(.{78}).*/\1/p'
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
||/ Name                                                  Version             
+++-=====================================================-====================
rc  bumblebee                                             3.2.1-5~xedgers~sauc
rc  dkms                                                  2.2.0.3-1.1ubuntu4  
rc  evolution-data-server-goa                             3.8.5-1ubuntu3      
rc  foomatic-filters                                      4.0.17-1ubuntu1     
rc  gmail-notify                                          1.6.1.1-3           
rc  gnome-control-center-datetime                         13.10.0+13.10.201310
rc  lib32gcc1                                             1:4.8.1-10ubuntu9   
rc  libamd2.2.0                                           1:3.4.0-3ubuntu1    
rc  libaudiofile1:amd64                                   0.3.6-2             
rc  libav-tools                                           6:0.8.9-0ubuntu0.13.
rc  libavcodec-extra-53:amd64                             6:0.8.13ubuntu0.13.1
rc  libavcodec53:amd64                                    6:0.8.9-0ubuntu0.13.
rc  libavdevice53:amd64                                   6:0.8.9-0ubuntu0.13.
rc  libavfilter2:amd64                                    6:0.8.9-0ubuntu0.13.
rc  libavformat-extra-53:amd64                            6:0.8.13ubuntu0.13.1
rc  libavformat53:amd64                                   6:0.8.9-0ubuntu0.13.
rc  libavutil-extra-51:amd64                              6:0.8.13ubuntu0.13.1
rc  libavutil51:amd64                                     6:0.8.9-0ubuntu0.13.
rc  libboost-date-time1.53.0:amd64                        1.53.0-6+exp3ubuntu8
rc  libboost-iostreams1.53.0:amd64                        1.53.0-6+exp3ubuntu8
rc  libboost-python1.53.0                                 1.53.0-6+exp3ubuntu8
rc  libboost-system1.53.0:amd64                           1.53.0-6+exp3ubuntu8
rc  libcamel-1.2-43                                       3.8.5-1ubuntu3      
rc  libcmis-0.3-3                                         0.3.1-3ubuntu1      
rc  libcogl-pango12:amd64                                 1.14.0-2            
rc  libcogl12:amd64                                       1.14.0-2            
rc  libcolamd2.7.1                                        1:3.4.0-3ubuntu1    
rc  libconfig++9:amd64                                    1.4.8-5             
rc  libcuda1-331                                          331.49-0ubuntu1~xedg
rc  libdb5.1:i386                                         5.1.29-7ubuntu1     
rc  libdns99                                              1:9.9.3.dfsg.P2-4ubu
rc  libdotconf1.0                                         1.0.13-3build2      
rc  libebackend-1.2-6                                     3.8.5-1ubuntu3      
rc  libebml3:amd64                                        1.2.2-2             
rc  libecal-1.2-15                                        3.8.5-1ubuntu3      
rc  libedata-book-1.2-17                                  3.8.5-1ubuntu3      
rc  libedata-cal-1.2-20                                   3.8.5-1ubuntu3      
rc  libedataserver-1.2-17                                 3.8.5-1ubuntu3      
rc  libffado2                                             2.1.0+svn2240-1ubunt
rc  libfftw3-long3:amd64                                  3.3.3-7ubuntu3      
rc  libglewmx1.8:amd64                                    1.9.0.is.1.8.0-0ubun
rc  libgoa-1.0-0:amd64                                    3.8.3-2             
rc  libgweather-3-3                                       3.8.2-0ubuntu1      
rc  libharfbuzz0a:amd64                                   0.9.19-1            
rc  libicu48:amd64                                        4.8.1.1-12ubuntu2   
rc  liblcms1:i386                                         1.19.dfsg-1.2ubuntu5
rc  libmatroska5:amd64                                    1.3.0-2             
rc  libmikmod2:amd64                                      3.1.12-5            
rc  libmjpegutils-2.0-0                                   1:2.0.0+debian-2ubun
rc  libmng1:amd64                                         1.0.10-3build1      
rc  libmpeg2encpp-2.0-0                                   1:2.0.0+debian-2ubun
rc  libmplex2-2.0-0                                       1:2.0.0+debian-2ubun
rc  libmysqlclient18:amd64                                5.5.40-0ubuntu0.14.0
rc  libnfs1:amd64                                         1.6.0-0~ppa1~trusty 
rc  libpcrecpp0:amd64                                     1:8.31-2ubuntu2     
rc  libpoppler43:amd64                                    0.24.1-0ubuntu1     
rc  libprocps0:amd64                                      1:3.3.3-2ubuntu9    
rc  libprotobuf-lite7                                     2.4.1-3ubuntu2      
rc  libprotobuf7                                          2.4.1-3ubuntu2      
rc  libprotoc7                                            2.4.1-3ubuntu2      
rc  libpython3.3:amd64                                    3.3.2-7ubuntu3.1    
rc  libpython3.3-minimal:amd64                            3.3.2-7ubuntu3.1    
rc  libqpdf10:amd64                                       4.2.0-2             
rc  libqt5core5:amd64                                     5.0.2+dfsg1-7ubuntu1
rc  libqt5v8-5:amd64                                      5.0.2-3             
rc  librhythmbox-core7                                    2.99.1-0ubuntu1     
rc  libshairplay0:amd64                                   0.9.0-6~trusty      
rc  libsidutils0                                          2.1.1-14            
rc  libsync-menu1:amd64                                   12.10.5+13.10.201310
rc  libtasn1-3:amd64                                      2.14-3              
rc  libtasn1-3:i386                                       2.14-3              
rc  libtotem-plparser17                                   3.4.5-1             
rc  libumfpack5.4.0                                       1:3.4.0-3ubuntu1    
rc  libunity-core-6.0-8                                   7.1.2+13.10.20131014
rc  libvdpau1:amd64                                       0.7-1               
rc  libvlccore5                                           2.0.8+git20140326+r4
rc  libwebp4:amd64                                        0.3.0-3             
rc  libx264-123:amd64                                     2:0.123.2189+git35cf
rc  libxatracker1:amd64                                   9.2.1-1ubuntu3      
rc  libxcb-dri3-0:amd64                                   1.10-2ubuntu1~xedger
rc  libxcb-dri3-0:i386                                    1.10-2ubuntu1~xedger
rc  libxcb-present0:amd64                                 1.10-2ubuntu1~xedger
rc  libxcb-present0:i386                                  1.10-2ubuntu1~xedger
rc  libxcb-sync0:amd64                                    1.9.1-3ubuntu1      
rc  libxcb-sync1:i386                                     1.10-2ubuntu1~xedger
rc  libxml++2.6-2                                         2.36.0-2            
rc  libxshmfence1:i386                                    1.1-2~xedgers~saucy1
rc  libxtst6:i386                                         2:1.2.2-1           
rc  linux-image-3.11.0-12-generic                         3.11.0-12.19        
rc  linux-image-3.11.0-13-generic                         3.11.0-13.20        
rc  linux-image-3.11.0-14-generic                         3.11.0-14.21        
rc  linux-image-3.11.0-15-generic                         3.11.0-15.25        
rc  linux-image-3.11.0-18-generic                         3.11.0-18.32        
rc  linux-image-3.11.0-19-generic                         3.11.0-19.33        
rc  linux-image-3.11.0-20-generic                         3.11.0-20.35        
rc  linux-image-3.11.0-22-generic                         3.11.0-22.38        
rc  linux-image-3.11.0-23-generic                         3.11.0-23.40        
rc  linux-image-3.11.0-24-generic                         3.11.0-24.42        
rc  linux-image-extra-3.11.0-12-generic                   3.11.0-12.19        
rc  linux-image-extra-3.11.0-13-generic                   3.11.0-13.20        
rc  linux-image-extra-3.11.0-14-generic                   3.11.0-14.21        
rc  linux-image-extra-3.11.0-15-generic                   3.11.0-15.25        
rc  linux-image-extra-3.11.0-18-generic                   3.11.0-18.32        
rc  linux-image-extra-3.11.0-19-generic                   3.11.0-19.33        
rc  linux-image-extra-3.11.0-20-generic                   3.11.0-20.35        
rc  linux-image-extra-3.11.0-22-generic                   3.11.0-22.38        
rc  linux-image-extra-3.11.0-23-generic                   3.11.0-23.40        
rc  linux-image-extra-3.11.0-24-generic                   3.11.0-24.42        
rc  mysql-common                                          5.5.40-0ubuntu0.14.0
rc  primus                                                0~20130601-1        
rc  python-ubuntuone-client                               13.10-0ubuntu1.2    
rc  python3.3                                             3.3.2-7ubuntu3.1    
rc  python3.3-minimal                                     3.3.2-7ubuntu3.1    
rc  rhythmbox                                             2.99.1-0ubuntu1     
rc  screen-resolution-extra                               0.15ubuntu1         
rc  transmission-gtk                                      2.82-0ubuntu1       
rc  ubuntuone-client                                      13.10-0ubuntu1.2    
rc  wine1.4                                               1:1.6.2-0ubuntu4    
rc  winff                                                 1.5.1-1             
rc  xbmc                                                  2:13.2~git20140711.1
rc  xserver-xorg-video-intel                              2:2.99.910+git201403
rc  xserver-xorg-video-radeon                             1:7.3.99+git20140206
rc  xserver-xorg-video-vmware                             1:13.0.1+git20140227
cory@CJS-XBMC:~$

```


Wasn't expecting this many unclean packages...

Thanks again for lending a hand on this!

---

### Post by mc4man on 2014-12-26
Add back  the xorgers ppa, & do a upgrade 
Then either continue to use the ppa or use ppa-purge on it.
In the future purge all ppa's before upgrading Ubuntu releases

---

### Post by schragge on 2014-12-26
> **Ozzmosis88 said:**
> ```

The following packages have unmet dependencies:
 libsdl2-2.0-0 : Depends: libwayland-egl1-mesa (>= 10.0.2) but it is not going to be installed or
                          libwayland-egl1
```
Lather, rinse, repeat. In other words,
```
sudo apt-get -f install lib{,wayland-}egl1-mesa
```

> I searched libwayland-egl1-mesa and found it is part of the edgers/ppa which caused some grief during the upgrade from 13.10 -> 14.04Well, [a version of libwayland-egl1-mesa]("http://packages.ubuntu.com/trusty/libwayland-egl1-mesa") is in trusty, too. So maybe the xorg-edgers PPA has nothing to do with it.

> Wasn't expecting this many unclean packages...Oh that's nothing serious, just some packages that were removed (**r**), but left some config files (**c**) after them laying about somewhere on system.

---

### Post by Ozzmosis88 on 2014-12-27
> **mc4man said:**
> Add back  the xorgers ppa, & do a upgrade 
Then either continue to use the ppa or use ppa-purge on it.
In the future purge all ppa's before upgrading Ubuntu releases

That did the trick. added the Edgers/PPA and performed update/upgrade, purged the PPA, update/upgrade, installed Kodi, and had to reinstall the Nvidia graphics drivers to get everything back to normal.

Thanks gents for the lending hand!

---

### Post by ray_silva on 2015-07-22
I know this thread is marked [SOLVED], and I'm sure it is for the original poster; however, I'm having the same problem with the same package, although a little bit different.

Here's my info:

```

ray@ray-OptiPlex-GX280:~$ sudo apt-get -f install libsdl2-2.0-0
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libglew1.6 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmicrohttpd5 libsdl2 libtiff4 libupstart1
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-image-3.13.0-46-generic linux-image-extra-3.13.0-46-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libsdl2-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0 B/321 kB of archives.
After this operation, 1,172 kB of additional disk space will be used.
(Reading database ... 370469 files and directories currently installed.)
Preparing to unpack .../libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb ...
Unpacking libsdl2-2.0-0:i386 (2.0.2+dfsg1-3ubuntu1.1) ...
dpkg: error processing archive /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/libSDL2-2.0.so.0', which is also in package libsdl2:i386 2.0.3+z4~20140315-8621-1ppa1precise1
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I also ran the 

```

dpkg -l|sed -nr '/^.[^in]/s/^(.{78}).*/\1/p' 

```

and got this:

```

| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
||/ Name                                                        Version       
+++-===========================================================-==============
rc  account-plugin-identica                                     0.11+14.04.201
rc  appmenu-gtk:i386                                            0.3.92-0ubuntu
rc  appmenu-gtk3:i386                                           0.3.92-0ubuntu
rc  checkbox                                                    0.17.6-0ubuntu
rc  consolekit                                                  0.4.5-3.1ubunt
rc  foomatic-filters                                            4.0.16-0ubuntu
rc  gnome-screensaver                                           3.6.1-0ubuntu1
rc  gs-cjk-resource                                             1.20100103-3  
rc  guile-1.8-libs                                              1.8.8+1-8ubunt
rc  gwibber                                                     3.4.2-0ubuntu2
rc  im-switch                                                   1.20ubuntu5.2 
rc  jockey-common                                               0.9.7-0ubuntu7
rc  jockey-gtk                                                  0.9.7-0ubuntu7
iU  kodi                                                        2:16.0~git2015
iU  kodi-bin                                                    2:16.0~git2015
rc  libapt-inst1.4:i386                                         0.8.16~exp12ub
rc  libarchive12:i386                                           3.0.3-6ubuntu1
rc  libavahi-ui-gtk3-0:i386                                     0.6.31-4ubuntu
rc  libavcodec53:i386                                           4:0.8.16-0ubun
rc  libavformat53:i386                                          4:0.8.16-0ubun
rc  libavutil51:i386                                            4:0.8.16-0ubun
rc  libbamf0:i386                                               0.2.126-0ubunt
rc  libbamf3-0:i386                                             0.2.126-0ubunt
rc  libbind9-80                                                 1:9.8.1.dfsg.P
rc  libboost-serialization1.46.1                                1.46.1-7ubuntu
rc  libbrlapi0.5                                                4.3-1ubuntu5  
rc  libcamel-1.2-29                                             3.2.3-0ubuntu7
rc  libcelt0-0                                                  0.7.1-1       
rc  libck-connector0:i386                                       0.4.5-3.1ubunt
rc  libcmis-0.2-0                                               0.1.0-1       
rc  libcupsdriver1:i386                                         1.5.3-0ubuntu8
rc  libcurl3-nss:i386                                           7.35.0-1ubuntu
rc  libdconf-dbus-1-0:i386                                      0.20.0-1      
rc  libdconf-qt0                                                0.0.0.110722-0
rc  libdconf0:i386                                              0.12.0-0ubuntu
rc  libdee-qt5-3:i386                                           3.3+14.04.2014
rc  libdiscid0:i386                                             0.6.1-2       
rc  libdns81                                                    1:9.8.1.dfsg.P
rc  libdotconf1.0                                               1.0.13-3      
rc  libdrm-nouveau1a:i386                                       2.4.52-1~preci
rc  libdvbpsi7                                                  0.2.2-1       
rc  libebackend-1.2-1                                           3.2.3-0ubuntu7
rc  libebml3:i386                                               1.2.2-2       
rc  libebook-1.2-12                                             3.2.3-0ubuntu7
rc  libecal-1.2-10                                              3.2.3-0ubuntu7
rc  libedata-book-1.2-11                                        3.2.3-0ubuntu7
rc  libedata-cal-1.2-13                                         3.2.3-0ubuntu7
rc  libedataserver-1.2-15                                       3.2.3-0ubuntu7
rc  libedataserverui-3.0-1                                      3.2.3-0ubuntu7
rc  libevince3-3                                                3.4.0-0ubuntu1
rc  libexiv2-11                                                 0.22-2        
rc  libexttextcat0                                              3.2.0-1ubuntu1
rc  libfftw3-long3:i386                                         3.3.3-7ubuntu3
rc  libgd2-xpm:i386                                             2.0.36~rc1~dfs
rc  libgdu-gtk0:i386                                            3.0.2-2ubuntu7
rc  libgdu0:i386                                                3.0.2-2ubuntu7
rc  libgexiv2-1                                                 0.4.1-1build1 
rc  libgl1-mesa-dri-lts-saucy:i386                              3:6           
rc  libglewmx1.6:i386                                           1.6.0-4       
rc  libgnome-bluetooth8                                         3.2.2-0ubuntu5
rc  libgnome-desktop-3-2                                        3.4.2-0ubuntu0
rc  libgnome-menu2                                              3.0.1-0ubuntu9
rc  libgnomekbd7                                                3.4.0.2-1ubunt
rc  libgoa-1.0-0:i386                                           3.4.0-0ubuntu1
rc  libgphoto2-2:i386                                           2.4.13-1ubuntu
rc  libgphoto2-port0:i386                                       2.4.13-1ubuntu
rc  libgrail5                                                   3.0.6-0ubuntu0
rc  libgtksourceview-3.0-0:i386                                 3.4.2-0ubuntu1
rc  libgtkspell-3-0                                             3.0.0~hg201108
rc  libgweather-3-0                                             3.4.1-0ubuntu1
rc  libgwibber-gtk2                                             3.4.2-0ubuntu2
rc  libgwibber2                                                 3.4.2-0ubuntu2
rc  libibus-1.0-0:i386                                          1.4.1-3ubuntu1
rc  libical0                                                    0.48-1ubuntu3 
rc  libicu48                                                    4.8.1.1-3ubunt
rc  libimobiledevice2                                           1.1.1-4       
rc  libindicate-gtk3                                            12.10.1-0ubunt
rc  libindicate5                                                12.10.1-0ubunt
rc  libindicator-messages-status-provider1                      0.6.0-0ubuntu2
rc  libisc83                                                    1:9.8.1.dfsg.P
rc  libisccc80                                                  1:9.8.1.dfsg.P
rc  libisccfg82                                                 1:9.8.1.dfsg.P
rc  libkpathsea5                                                2009-11ubuntu2
rc  liblaunchpad-integration-3.0-1                              0.1.56.1      
rc  liblcms1:i386                                               1.19.dfsg-1.2u
rc  libllvm3.3:i386                                             1:3.3-16ubuntu
rc  liblua5.1-0:i386                                            5.1.5-5ubuntu0
rc  liblwres80                                                  1:9.8.1.dfsg.P
rc  libmatroska5                                                1.3.0-1       
rc  libmetacity-private0                                        1:2.34.1-1ubun
rc  libmng1:i386                                                1.0.10-3      
rc  libmpc2:i386                                                0.9-4         
rc  libmusicbrainz3-6                                           3.0.2-2.1     
rc  libnux-2.0-0                                                2.14.1-0ubuntu
rc  libopenspc0                                                 0.3.99a-2     
rc  liboverlay-scrollbar-0.2-0                                  0.2.16-0ubuntu
rc  liboverlay-scrollbar3-0.2-0                                 0.2.16-0ubuntu
rc  libpackagekit-glib2-14                                      0.7.2-4ubuntu3
rc  libpoppler19:i386                                           0.18.4-1ubuntu
rc  libprotobuf7                                                2.4.1-1ubuntu2
rc  libprotoc7                                                  2.4.1-1ubuntu2
rc  libprotoc8:i386                                             2.5.0-9ubuntu1
rc  libpth20:i386                                               2.0.7-19ubuntu
rc  libqtbamf1                                                  0.2.4-0ubuntu2
rc  libqtdee2                                                   0.2.4-0ubuntu1
rc  libqtgconf1                                                 0.1-0ubuntu5  
rc  libquvi7:i386                                               0.4.1-1ubuntu3
rc  libraw5                                                     0.14.4-0ubuntu
rc  librhythmbox-core5                                          2.96-0ubuntu4.
rc  libslp1                                                     1.2.1-9       
rc  libsnmp15                                                   5.4.3~dfsg-2.4
rc  libstlport4.6ldbl                                           4.6.2-7       
rc  libsyncdaemon-1.0-1                                         3.0.2-0ubuntu2
rc  libsysfs2:i386                                              2.1.0+repack-3
rc  libtasn1-3:i386                                             2.10-1ubuntu1.
rc  libtelepathy-farstream2:i386                                0.4.0-3ubuntu2
rc  libtelepathy-logger2:i386                                   0.4.0-0ubuntu1
rc  libtotem-plparser17                                         3.4.1-1       
rc  libu1db-qt5-3:i386                                          0.1.5+14.04.20
rc  libunique-3.0-0                                             3.0.2-2ubuntu1
rc  libunity-core-5.0-5                                         5.20.0-0ubuntu
rc  libupnp3                                                    1:1.6.6-5.1ubu
rc  libusbmuxd1                                                 1.0.7-2ubuntu0
rc  libvlccore5                                                 2.0.8-0ubuntu0
rc  libwayland-ltss-client0:i386                                1.1.0-2ubuntu3
rc  libwayland-ltss-server0:i386                                1.1.0-2ubuntu3
rc  libx264-120:i386                                            2:0.120.2151+g
rc  libxrandr-ltss2:i386                                        2:1.4.0-1ubunt
rc  libyajl1                                                    1.0.12-2      
rc  linux-image-3.11.0-15-generic                               3.11.0-15.25~p
rc  python-apport                                               2.14.1-0ubuntu
rc  python-aptdaemon.pkcompat                                   0.43+bzr805-0u
rc  python-central                                              0.6.17ubuntu2 
rc  python-ubuntuone-client                                     3.0.2-0ubuntu2
rc  python-ubuntuone-storageprotocol                            3.0.2-0ubuntu1
rc  ubuntuone-client                                            3.0.2-0ubuntu2
rc  unity-common                                                5.20.0-0ubuntu
rc  xserver-xorg-video-vmware-lts-saucy                         3:6           

```

Can I get a little help on fixing this?

---

