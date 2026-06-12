---
title: "Can't update anything in terminal repository messed up new please help"
date: 2020-03-27
forum: General Help
---

### Post by jp2020 on 2020-03-27
Hi I am completely new to all of this I can't update repositories at all I don't know what I've messed up could someone please guide me step by step on what to do I've tried myself troubleshooting but I'm lost. Here's what I'm seeing....


```
brian@brian-pc:~$ sudo apt-get install software-properties-common
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
software-properties-common is already the newest version (0.96.27.1).
0 upgraded, 0 newly installed, 0 to remove and 144 not upgraded.
brian@brian-pc:~$ sudo add-apt-repository ppa:team-xbmc/ppa
 Official Team Kodi stable releases
 More info: [https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa](https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa)
Press [ENTER] to continue or Ctrl-c to cancel adding it.


Hit:1 [http://archive.canonical.com](http://archive.canonical.com) cosmic InRelease                         
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease           
Hit:3 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) cosmic InRelease                
Ign:4 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) cosmic InRelease       
Hit:5 [http://ppa.launchpad.net/morphis/anbox-support/ubuntu](http://ppa.launchpad.net/morphis/anbox-support/ubuntu) cosmic InRelease
Err:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security Release             
  404  Not Found [IP: 91.189.88.152 80]
Hit:7 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) cosmic InRelease        
Err:8 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) cosmic Release         
  404  Not Found [IP: 91.189.95.83 80]
Ign:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic InRelease                     
Ign:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-updates InRelease            
Hit:11 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease
Ign:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-backports InRelease
Err:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic Release
  404  Not Found [IP: 91.189.88.152 80]
Err:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-updates Release
  404  Not Found [IP: 91.189.88.152 80]
Err:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-backports Release
  404  Not Found [IP: 91.189.88.152 80]
Reading package lists... Done
W: Skipping acquire of configured file 'partner/source/Sources' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/binary-amd64/Packages' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/i18n/Translation-en' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/i18n/Translation-en_US' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/Components-amd64.yml' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/icons-48x48.tar' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/icons-64x64.tar' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/icons-64x64@2.tar' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/icons-128x128.tar' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/cnf/Commands-amd64' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
E: The repository 'http://security.ubuntu.com/ubuntu cosmic-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/gezakovacs/ppa/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list:2 and /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list:2 and /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list:4
brian@brian-pc:~$ sudo apt-get update
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic InRelease                     
Ign:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-updates InRelease             
Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-backports InRelease
Err:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic Release
  404  Not Found [IP: 91.189.88.142 80]
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-updates Release
  404  Not Found [IP: 91.189.88.142 80]
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-backports Release
  404  Not Found [IP: 91.189.88.142 80]
Hit:7 [http://archive.canonical.com](http://archive.canonical.com) cosmic InRelease                         
Ign:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease           
Hit:9 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) cosmic InRelease                
Hit:10 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                  
Err:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security Release          
  404  Not Found [IP: 91.189.88.152 80]
Ign:12 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) cosmic InRelease
Hit:13 [http://ppa.launchpad.net/morphis/anbox-support/ubuntu](http://ppa.launchpad.net/morphis/anbox-support/ubuntu) cosmic InRelease
Hit:14 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) cosmic InRelease       
Err:15 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) cosmic Release        
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done                      
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Skipping acquire of configured file 'partner/source/Sources' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/binary-amd64/Packages' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/i18n/Translation-en_US' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/i18n/Translation-en' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/Components-amd64.yml' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/icons-48x48.tar' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/icons-64x64.tar' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/icons-64x64@2.tar' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/dep11/icons-128x128.tar' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'partner/cnf/Commands-amd64' as repository 'http://old-releases.ubuntu.com/ubuntu cosmic InRelease' doesn't have the component 'partner' (component misspelt in sources.list?)
E: The repository 'http://security.ubuntu.com/ubuntu cosmic-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/gezakovacs/ppa/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list:2 and /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list:2 and /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list:4
brian@brian-pc:~$ sudo apt-get install kodi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  kodi-inputstream-adaptive kodi-inputstream-rtmp kodi-peripheral-joystick
  kodi-x11 libcec4 libcrossguid0 libfstrcmp0 libmicrohttpd12
  libp8-platform2 libshairplay0 mesa-utils python-bluez python-olefile
  python-pil python-pycryptodome python-simplejson
Suggested packages:
  kodi-pvr-mythtv kodi-pvr-vdr-vnsi kodi-pvr-tvheadend-hts
  kodi-pvr-dvbviewer kodi-pvr-iptvsimple kodi-audioencoder-vorbis
  kodi-audioencoder-flac kodi-audioencoder-lame python-pil-doc
  python-pil-dbg
The following NEW packages will be installed:
  kodi kodi-inputstream-adaptive kodi-inputstream-rtmp
  kodi-peripheral-joystick kodi-x11 libcec4 libcrossguid0 libfstrcmp0
  libmicrohttpd12 libp8-platform2 libshairplay0 mesa-utils python-bluez
  python-olefile python-pil python-pycryptodome python-simplejson
0 upgraded, 17 newly installed, 0 to remove and 144 not upgraded.
Need to get 5,108 kB/39.9 MB of archives.
After this operation, 106 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic/universe amd64 python-pycryptodome amd64 3.6.1-2build1
  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/p/pycryptodome/python-pycryptodome_3.6.1-2build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/pycryptodome/python-pycryptodome_3.6.1-2build1_amd64.deb)  404  Not Found [IP: 91.189.88.152 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```


Any help is greatly appreciated. Thanks.

---

### Post by guiverc on 2020-03-27
Ubuntu 18.10 is EOL or *end-of-life* ([http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/](http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/)

It was an interim or standard release, and *release-upgraded *to Ubuntu 19.04, so you should have upgraded before it reached end-of-life.

The 18.10 means 2018-October release; it's supported life was 9 months, and since it upgraded to 19.04 or the 2019-April release, you had 3 months to move to that release. That upgrade however is gone, as Ubuntu 19.04 is now also EOL with it's users having upgraded to 19.10 (2019-October) release.

Use a LTS or *long-term-support* release if you don't like *release-upgrading* every 6-9 months

This will be useful - [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

but in your case, I'd likely backup your data, and re-install a supported release. I don't know what you use your machine for, nor if you want to avoid 6-9 month release-upgrades (thus LTS releases make more sense having 2-5 year upgrade cycles), but that would be my suggestion (esp. a *something-else* install, using existing partitions without format to minimize configuration of your system)

---

### Post by DuckHook on 2020-03-27
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

