---
title: "Software Updater"
date: 2017-08-16
forum: General Help
---

### Post by AnupamMitra on 2017-08-16
My OS is Ubuntu 16.04. Software Updater was working properly till yesterday. Yesterday Software Updater itself updated. It might be coincident, but since then it appeared several times but failed to complete its job with an advice to check internet connection. But my internet connection was quite okay. However, I tried to update through Terminal manually, but couldn't succeed. The outcome is given hereunder. ```
 
anupam@anupam:~$ sudo apt update
[sudo] password for anupam: 
Hit:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:3 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu xenial InRelease       
Hit:4 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial InRelease       
Hit:5 http://ppa.launchpad.net/pipelight/stable/ubuntu xenial InRelease        
Hit:6 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease        
Hit:7 http://in.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:8 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:9 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:10 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Fetched 306 kB in 22s (13.8 kB/s)  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
13 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target Translations (contrib/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target DEP-11 (contrib/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target Translations (contrib/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target DEP-11 (contrib/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target Translations (contrib/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target DEP-11 (contrib/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target Translations (contrib/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target DEP-11 (contrib/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target Translations (contrib/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target DEP-11 (contrib/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target Translations (contrib/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target DEP-11 (contrib/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:56
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target Translations (contrib/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target DEP-11 (contrib/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:57
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target Translations (contrib/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target DEP-11 (contrib/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:58
anupam@anupam:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-83 linux-headers-4.4.0-83-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-image-4.4.0-83-generic
  linux-image-4.4.0-87-generic linux-image-extra-4.4.0-83-generic
  linux-image-extra-4.4.0-87-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.4.0-92 linux-headers-4.4.0-92-generic
  linux-image-4.4.0-92-generic linux-image-extra-4.4.0-92-generic
The following packages will be upgraded:
  firefox firefox-locale-bn firefox-locale-en gnome-software
  gnome-software-common libgd3 linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev snapd ubuntu-software xul-ext-ubufox
13 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.5 MB/124 MB of archives.
After this operation, 291 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-4.4.0-92-generic i386 4.4.0-92.115
  Connection failed [IP: 91.189.88.149 80]
Err:1 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-4.4.0-92-generic i386 4.4.0-92.115
  Connection failed [IP: 91.189.88.149 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-92-generic_4.4.0-92.115_i386.deb  Connection failed [IP: 91.189.88.149 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
anupam@anupam:~$ ^C
anupam@anupam:~$ 

```
Need opinions and suggestions from the experts.

---

### Post by Andreyshel on 2017-08-16
Okey.
Let`s try quite simple thing.
Can you download the package when you go to [COLOR=#000000][FONT=&quot]http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-92-generic_4.4.0-92.115_i386.deb [/FONT][/COLOR][COLOR=#000000]with your browser?[/COLOR]

---

### Post by AnupamMitra on 2017-08-16
> **Andreyshel said:**
> Okey.
Let`s try quite simple thing.
Can you download the package when you go to [COLOR=#000000][FONT=&amp]http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-92-generic_4.4.0-92.115_i386.deb [/FONT][/COLOR][COLOR=#000000]with your browser?[/COLOR]

Yes, it could be downloaded with browser and saved. It is linux-image-4.4.0-92-generic and it appears through Ubuntu Software and asking me to install. Should I install it ?

---

### Post by Andreyshel on 2017-08-16
Does problem remain if  you try to install this package with [COLOR=#000000][FONT=&amp]sudo apt-get upgrade?[/FONT][/COLOR][FONT=Ubuntu Mono][COLOR=#000000]
[/COLOR][/FONT]I think that security.ubuntu.com  just could be temporary down


> [COLOR=#000000]Should I install it ?[/COLOR]
No it was a connectivity test.

---

### Post by AnupamMitra on 2017-08-16
> **Andreyshel said:**
> Does problem remain if  you try to install this package with [COLOR=#000000][FONT=&amp]sudo apt-get upgrade[/FONT][/COLOR][FONT=Ubuntu Mono][COLOR=#000000]
[/COLOR][/FONT]I think that security.ubuntu.com  just could be temporary down



No it was a connectivity test.

Okay, thanks for your cooperation and quick response.

---

### Post by Bashing-om on 2017-08-16
AgoAnupamMitra; Hello;

The package manager is telling you IT has a problem, and request your guidance as to what to do:
> 
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list:55


So what we do is look at this sources list and remove the conflict.
Post back 
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
and we see what to do about lines 54 and 55 .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by AnupamMitra on 2017-08-17
> **Bashing-om said:**
> AgoAnupamMitra; Hello;

The package manager is telling you IT has a problem, and request your guidance as to what to do:


So what we do is look at this sources list and remove the conflict.
Post back 
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
and we see what to do about lines 54 and 55 .
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Bashing-om - Thanks for your cooperation. The outcome is given below.
```

anupam@anupam:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release i386 (20160719)]/ xenial main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://in.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    # deb-src http://in.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://in.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11    # deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team, and may not be under a free licence. Please satisfy yourself as to
    15    ## your rights to use the software. Also, please note that software in
    16    ## universe WILL NOT receive any review or updates from the Ubuntu security
    17    ## team.
    18    deb http://in.archive.ubuntu.com/ubuntu/ xenial universe
    19    # deb-src http://in.archive.ubuntu.com/ubuntu/ xenial universe
    20    deb http://in.archive.ubuntu.com/ubuntu/ xenial-updates universe
    21    # deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates universe
    22    
    23    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24    ## team, and may not be under a free licence. Please satisfy yourself as to 
    25    ## your rights to use the software. Also, please note that software in 
    26    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27    ## security team.
    28    deb http://in.archive.ubuntu.com/ubuntu/ xenial multiverse
    29    # deb-src http://in.archive.ubuntu.com/ubuntu/ xenial multiverse
    30    deb http://in.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    31    # deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    32    
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    deb http://in.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    39    # deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    deb http://archive.canonical.com/ubuntu xenial partner
    46    deb-src http://archive.canonical.com/ubuntu xenial partner
    47    
    48    deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    49    # deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    50    deb http://security.ubuntu.com/ubuntu xenial-security universe
    51    # deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    52    deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    53    # deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    54    deb http://download.virtualbox.org/virtualbox/debian xenial contrib
    55    deb http://download.virtualbox.org/virtualbox/debian xenial contrib
    56    deb http://download.virtualbox.org/virtualbox/debian xenial contrib
    57    deb http://download.virtualbox.org/virtualbox/debian xenial contrib
    58    deb http://download.virtualbox.org/virtualbox/debian xenial contrib
    59    
    60    
anupam@anupam:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/clipgrab-team-ubuntu-ppa-xenial.list <==
deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/clipgrab-team-ubuntu-ppa-xenial.list.save <==
deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list <==
deb http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
# deb-src http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
# deb-src http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
# deb-src http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main

==> /etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list.save <==
deb http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
# deb-src http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
# deb-src http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list <==
deb http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list.save <==
deb http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main

==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list <==
deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main

==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list.save <==
deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
anupam@anupam:~$ 

```

---

### Post by Bashing-om on 2017-08-17
AnupamMitra; Hey;

The simple fix is to remove those duplicated lines.
As to why the duplicates.. only you can guess .

Anyway backup what you have - never can tell what might happen - power outage can hurt real bad !
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-16aug2017

```

and in your favorite text editor open up that sources.list file.
Here I use gedit:
```

sudo -H gedit /etc/apt/sources.list

```
now delete (cut) lines 55 through and including line 60 .
Once looked at again and satisfied with the edit; save the file and
exit the text editor.
Now what results:
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]maybe done now
[INDENT][INDENT][/INDENT]maybe not
[/INDENT][/INDENT][/INDENT]

---

### Post by AnupamMitra on 2017-08-17
> **Bashing-om said:**
> AnupamMitra; Hey;

The simple fix is to remove those duplicated lines.
As to why the duplicates.. only you can guess .

Anyway backup what you have - never can tell what might happen - power outage can hurt real bad !
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-16aug2017

```

and in your favorite text editor open up that sources.list file.
Here I use gedit:
```

sudo -H gedit /etc/apt/sources.list

```
now delete (cut) lines 55 through and including line 60 .
Once looked at again and satisfied with the edit; save the file and
exit the text editor.
Now what results:
```

sudo apt update
sudo apt upgrade

```
[INDENT][INDENT]maybe done now[INDENT]maybe not
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om - Hi, I applied what you have suggested, but it still stuck in the same position. However, the outcome is hereunder. 
```

anupam@anupam:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list-16aug2017
[sudo] password for anupam: 
anupam@anupam:~$ sudo -H gedit /etc/apt/sources.list

(gedit:5423): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:5423): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:5423): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:5423): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
anupam@anupam:~$ sudo apt update
Hit:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:3 http://in.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:4 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:6 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Hit:7 http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu xenial InRelease       
Hit:8 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/pipelight/stable/ubuntu xenial InRelease
Hit:10 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Fetched 306 kB in 36s (8,508 B/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
13 packages can be upgraded. Run 'apt list --upgradable' to see them.
anupam@anupam:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-83 linux-headers-4.4.0-83-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-image-4.4.0-83-generic
  linux-image-4.4.0-87-generic linux-image-extra-4.4.0-83-generic
  linux-image-extra-4.4.0-87-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.4.0-92 linux-headers-4.4.0-92-generic
  linux-image-4.4.0-92-generic linux-image-extra-4.4.0-92-generic
The following packages will be upgraded:
  firefox firefox-locale-bn firefox-locale-en gnome-software
  gnome-software-common libgd3 linux-generic linux-headers-generic
  linux-image-generic linux-libc-dev snapd ubuntu-software xul-ext-ubufox
13 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.5 MB/124 MB of archives.
After this operation, 291 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
86% [Waiting for headers]                                                      

```

---

### Post by Bashing-om on 2017-08-17
AnupamMitra; Humm ???

All looks great up and until :
> 
86% [Waiting for headers]

Is the system hung here waiting ?

[INDENT][INDENT]just do not know
[/INDENT][/INDENT]

---

### Post by AnupamMitra on 2017-08-17
> **Bashing-om said:**
> AnupamMitra; Humm ???

All looks great up and until :

Is the system hung here waiting ?
[INDENT][INDENT]just do not know
[/INDENT]
[/INDENT]


Bashing-om: Yes, you are absolutely correct.

---

### Post by Bashing-om on 2017-08-17
AnupamMitra; Hummm ..

Could be from a number of causes; 
See:
[https://askubuntu.com/questions/156650/apt-get-update-very-slow-stuck-at-waiting-for-headers](https://askubuntu.com/questions/156650/apt-get-update-very-slow-stuck-at-waiting-for-headers)

Maybe the sources.list file is corrupted .. just a maybe.

[INDENT][INDENT]sometimes this
[INDENT][INDENT][INDENT]other times that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by AnupamMitra on 2017-08-17
> **Bashing-om said:**
> AnupamMitra; Hummm ..

Could be from a number of causes; 
See:
[https://askubuntu.com/questions/156650/apt-get-update-very-slow-stuck-at-waiting-for-headers](https://askubuntu.com/questions/156650/apt-get-update-very-slow-stuck-at-waiting-for-headers)

Maybe the sources.list file is corrupted .. just a maybe.[INDENT][INDENT]sometimes this[INDENT][INDENT][INDENT]other times that
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om: At last the battle is over! According to the advice given in the above link, I did the following.
```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update  

```
Thereafter Software Updater appeared and asked to download several applications of around 125 MB. I allowed the same and finally now it is settled. Thanks for your continuous support.

---

### Post by Bashing-om on 2017-08-17
AnupamMitra; Outstanding .

-You- do good work :)
Pleased to be of some help.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

