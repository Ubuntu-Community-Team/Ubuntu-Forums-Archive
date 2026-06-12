---
title: "Second Time Reinstalling Ubuntu, still getting dependencies error! Please Help!"
date: 2016-05-29
forum: General Help
---

### Post by kwanbis on 2016-05-29
I have been reinstalling Ubuntu after some issues with Cinnamon.

But I'm getting this error:

```
~$ sudo apt install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 google-chrome-stable : Depends: libappindicator1 but it is not going to be installed
 opera-stable:i386 : PreDepends: apt-transport-https:i386 but it is not going to be installed
                     Depends: libasound2:i386 (>= 1.0.16)
                     Depends: libatk1.0-0:i386 (>= 1.12.4) but it is not going to be installed
                     Depends: libc6:i386 (>= 2.11) but it is not going to be installed
                     Depends: libcairo2:i386 (>= 1.6.0) but it is not going to be installed
                     Depends: libcups2:i386 (>= 1.4.0) but it is not going to be installed
                     Depends: libcurl3:i386 (>= 7.16.2) but it is not going to be installed
                     Depends: libdbus-1-3:i386 (>= 1.2.14) but it is not going to be installed
                     Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                     Depends: libfontconfig1:i386 (>= 2.8.0) but it is not going to be installed
                     Depends: libgcc1:i386 (>= 1:4.1.1) but it is not going to be installed
                     Depends: libgconf-2-4:i386 (>= 2.31.1) but it is not going to be installed
                     Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                     Depends: libglib2.0-0:i386 (>= 2.31.8) but it is not going to be installed
                     Depends: libgtk2.0-0:i386 (>= 2.24.0) but it is not going to be installed
                     Depends: libnotify4:i386 (>= 0.7.0) but it is not going to be installed
                     Depends: libpango1.0-0:i386 (>= 1.14.0) but it is not going to be installed
                     Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
                     Depends: libx11-6:i386 (>= 2:1.4.99.1) but it is not going to be installed
                     Depends: libxcomposite1:i386 (>= 1:0.3-1) but it is not going to be installed
                     Depends: libxcursor1:i386 (> 1.1.2) but it is not going to be installed
                     Depends: libxdamage1:i386 (>= 1:1.1) but it is not going to be installed
                     Depends: libxext6:i386 but it is not going to be installed
                     Depends: libxfixes3:i386 but it is not going to be installed
                     Depends: libxi6:i386 (>= 2:1.2.99.4) but it is not going to be installed
                     Depends: libxrandr2:i386 (>= 2:1.2.99.2) but it is not going to be installed
                     Depends: libxrender1:i386 but it is not going to be installed
                     Depends: libxss1:i386 but it is not going to be installed
                     Depends: libxtst6:i386 but it is not going to be installed
                     Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
                     Depends: libudev0:i386 (>= 147) but it is not going to be installed or
                              libudev1:i386 (>= 183) but it is not going to be installed
                     Depends: libnspr4:i386 (>= 1.8.0.10) but it is not going to be installed
                     Depends: libnss3:i386 (>= 3.14.3) but it is not going to be installed
                     Recommends: pepperflashplugin-nonfree:i386 but it is not going to be installed
                     Recommends: chromium-codecs-ffmpeg-extra:i386 but it is not going to be installed
 synaptic : Depends: libept1.5.0 but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
 vivaldi-stable : Depends: libappindicator1 but it is not going to be installed
                  Recommends: pepperflashplugin-nonfree but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

What can I do?

The only commands I have run are:

```
SET ALL REPOS
sudo add-apt-repository main && sudo add-apt-repository universe && sudo add-apt-repository restricted && sudo add-apt-repository multiverse

UPDATE UPGRADE
sudo apt-get update && sudo apt-get upgrade

INSTALL GDEBI
sudo apt install gdebi

INSTALL CINNAMON
sudo add-apt-repository ppa:embrosyn/cinnamon && sudo apt update && sudo apt install cinnamon

FIX LOGOUT IN CINNAMON
gsettings set org.cinnamon.desktop.session settings-daemon-uses-logind true && gsettings set org.cinnamon.desktop.session session-manager-uses-logind true && gsettings set org.cinnamon.desktop.session screensaver-uses-logind false

INSTALL NUMIX THEME
sudo apt install numix-gtk-theme

INSTALL CHROMIUM
sudo apt install chromium-browser

INSTALL CHROME
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb && sudo dpkg -i --force-depends google-chrome-stable_current_amd64.deb

INSTALL OPERA
wget http://operasoftware.pc.cdn.bitgravity.com/pub/opera/desktop/36.0.2130.32/linux/opera-stable_36.0.2130.32_i386.deb && sudo dpkg -i --force-depends opera-stable_36.0.2130.32_i386.deb

INSTALL VIVALDI
wget https://downloads.vivaldi.com/stable/vivaldi-stable_1.1.453.47-1_amd64.deb && sudo dpkg -i --force-depends vivaldi-stable_1.1.453.47-1_amd64.deb

INSTALL VLC
sudo apt install vlc browser-plugin-vlc

INSTALL DOUBLE COMMANDER
sudo add-apt-repository ppa:alexx2000/doublecmd && sudo apt-get update && sudo apt-get install doublecmd-gtk

INSTALL SIMPLENOTE
Download .deb
sudo dpkg -i --force-depends simplenote-1.0.1.deb
```

---

### Post by CantankRus on 2016-05-29
What PPAs are enabled?
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by kwanbis on 2016-05-29
> **CantankRus said:**
> What PPAs are enabled?
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

Thanks for helping:

```
/etc/apt/sources.list:deb http://co.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://co.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://co.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://co.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://co.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://co.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://co.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list:deb http://mirror.fsf.org/trisquel/ toutatis-updates main
/etc/apt/sources.list.d/alexx2000-ubuntu-doublecmd-xenial.list:deb http://ppa.launchpad.net/alexx2000/doublecmd/ubuntu xenial main
/etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list:deb http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/nowrep-ubuntu-qupzilla-xenial.list:deb http://ppa.launchpad.net/nowrep/qupzilla/ubuntu xenial main
/etc/apt/sources.list.d/opera-stable.list:deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/vivaldi.list:deb http://repo.vivaldi.com/stable/deb/ stable main

```

---

### Post by CantankRus on 2016-05-30
What do you use "**deb [http://mirror.fsf.org/trisquel/](http://mirror.fsf.org/trisquel/) toutatis-updates main**" repo  for? 
I enabled it and it contains an update to the package **base-files**.
After upgrading base-files, software-properties-gtk would not open.

Maybe this ppa is the source of your problems.
I downgraded back to the default ubuntu version of  **base-files** and all works fine again.

This shows after downgrading **base-files**.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt-cache policy base-files**
base-files:
  Installed: 9.4ubuntu4
  Candidate: 1:6.5ubuntu6.8+6.0.1trisquel5
  Version table:
     1:6.5ubuntu6.8+6.0.1trisquel5 500
        500 http://mirror.fsf.org/trisquel toutatis-updates/main amd64 Packages
 *** 9.4ubuntu4 500
        500 http://ftp.iinet.net.au/pub/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by kwanbis on 2016-05-30
> **CantankRus said:**
> What do you use "**deb [http://mirror.fsf.org/trisquel/](http://mirror.fsf.org/trisquel/) toutatis-updates main**" repo  for? 
I enabled it and it contains an update to the package **base-files**.
After upgrading base-files, software-properties-gtk would not open.
I have no idea, and I don't remember adding it. I don't see it on any of my commands. But I removed the repo, updated, and tried to install synaptic and I get:

```
xxx@U520:~$ sudo apt update
[sudo] password for xxx: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:3 http://ppa.launchpad.net/alexx2000/doublecmd/ubuntu xenial InRelease     
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:6 http://co.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:7 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial InRelease       
Get:8 http://co.archive.ubuntu.com/ubuntu xenial-updates InRelease [94,5 kB]   
Ign:10 http://repo.vivaldi.com/stable/deb stable InRelease                     
Hit:11 http://ppa.launchpad.net/nowrep/qupzilla/ubuntu xenial InRelease        
Hit:12 http://repo.vivaldi.com/stable/deb stable Release                       
Hit:14 http://co.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Hit:15 https://deb.opera.com/opera-stable stable InRelease
Fetched 94,5 kB in 1s (71,0 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
javier@U520:~$ sudo apt install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 google-chrome-stable : Depends: libappindicator1 but it is not going to be installed
 opera-stable:i386 : PreDepends: apt-transport-https:i386 but it is not going to be installed
                     Depends: libasound2:i386 (>= 1.0.16)
                     Depends: libatk1.0-0:i386 (>= 1.12.4) but it is not going to be installed
                     Depends: libc6:i386 (>= 2.11) but it is not going to be installed
                     Depends: libcairo2:i386 (>= 1.6.0) but it is not going to be installed
                     Depends: libcups2:i386 (>= 1.4.0) but it is not going to be installed
                     Depends: libcurl3:i386 (>= 7.16.2) but it is not going to be installed
                     Depends: libdbus-1-3:i386 (>= 1.2.14) but it is not going to be installed
                     Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                     Depends: libfontconfig1:i386 (>= 2.8.0) but it is not going to be installed
                     Depends: libgcc1:i386 (>= 1:4.1.1) but it is not going to be installed
                     Depends: libgconf-2-4:i386 (>= 2.31.1) but it is not going to be installed
                     Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                     Depends: libglib2.0-0:i386 (>= 2.31.8) but it is not going to be installed
                     Depends: libgtk2.0-0:i386 (>= 2.24.0) but it is not going to be installed
                     Depends: libnotify4:i386 (>= 0.7.0) but it is not going to be installed
                     Depends: libpango1.0-0:i386 (>= 1.14.0) but it is not going to be installed
                     Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
                     Depends: libx11-6:i386 (>= 2:1.4.99.1) but it is not going to be installed
                     Depends: libxcomposite1:i386 (>= 1:0.3-1) but it is not going to be installed
                     Depends: libxcursor1:i386 (> 1.1.2) but it is not going to be installed
                     Depends: libxdamage1:i386 (>= 1:1.1) but it is not going to be installed
                     Depends: libxext6:i386 but it is not going to be installed
                     Depends: libxfixes3:i386 but it is not going to be installed
                     Depends: libxi6:i386 (>= 2:1.2.99.4) but it is not going to be installed
                     Depends: libxrandr2:i386 (>= 2:1.2.99.2) but it is not going to be installed
                     Depends: libxrender1:i386 but it is not going to be installed
                     Depends: libxss1:i386 but it is not going to be installed
                     Depends: libxtst6:i386 but it is not going to be installed
                     Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
                     Depends: libudev0:i386 (>= 147) but it is not installable or
                              libudev1:i386 (>= 183) but it is not going to be installed
                     Depends: libnspr4:i386 (>= 1.8.0.10) but it is not going to be installed
                     Depends: libnss3:i386 (>= 3.14.3) but it is not going to be installed
                     Recommends: pepperflashplugin-nonfree:i386 but it is not going to be installed
                     Recommends: chromium-codecs-ffmpeg-extra:i386 but it is not going to be installed
 synaptic : Depends: libept1.5.0 but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
 vivaldi-stable : Depends: libappindicator1 but it is not going to be installed
                  Recommends: pepperflashplugin-nonfree but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Do I need to do anything else?

EDIT: I believe I tried to install IceCat, but I'm almost positive it was before the second reinstall but I can be wrong. Anyway, I uninstalled it and still that error.

---

### Post by CantankRus on 2016-05-30
Disabling/removing a ppa doesn't uninstall packages you may have installed from that ppa.
You need to purge the ppa using ppa-purge.
I'm not sure of the correct syntax to purge a ppa not from launchpad.

.....and I'm not entirely sure would fix when you are not sure what you have done.
It seems to be a problem from added ppas though.

Did you try the message from your "sudo apt update" output....
```
sudo apt-get -f install
```

---

### Post by mc4man on 2016-05-30
Your issue stems from using dpkg with --force-depends on wrong arch packages, in particular opera. It's likely the 1st time you did this it went ahead without satisfying the pre-depends, now things are borked.
You could check that with sudo apt-get -f install which should inform you that you are requesting  to do a dangerous thing, ect.

I'd say a 3rd install, (64 bit), then if installing a downloaded .deb use just plain apt, ie.
sudo apt install /path/to/downloaded.deb
(- and no need to install wrong arch browsers

---

### Post by kwanbis on 2016-05-30
> **CantankRus said:**
> Disabling/removing a ppa doesn't uninstall packages you may have installed from that ppa. 
You need to purge the ppa using ppa-purge. I'm not sure of the correct syntax to purge a ppa not from launchpad. .....and I'm not entirely sure would fix when you are not sure what you have done. It seems to be a problem from added ppas though. Did you try the message from your "sudo apt update" output....
```
sudo apt-get -f install
```

> **mc4man said:**
> Your issue stems from using dpkg with --force-depends on wrong arch packages, in particular opera. It's likely the 1st time you did this it went ahead without satisfying the pre-depends, now things are borked. You could check that with sudo apt-get -f install which should inform you that you are requesting  to do a dangerous thing, ect. I'd say a 3rd install, (64 bit), then if installing a downloaded .deb use just plain apt, ie. sudo apt install /path/to/downloaded.deb
(- and no need to install wrong arch browsers
So it seems the problem was actually the opera .deb. I was using Opera 36 and the latest is Opera 37.

I don't get why don't they have a opera_latest.deb instead of different opera_version36.deb

So, I reinstalled all and so far I have run all this commands without issues:

```
SAVE GRUB IN DISK B
sudo grub-install /dev/sdb
sudo update-grub

SET ALL REPOS
sudo add-apt-repository main && sudo add-apt-repository universe && sudo add-apt-repository restricted && sudo add-apt-repository multiverse

ENABLE PARTNERS ???
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"

UPDATE UPGRADE
sudo apt-get update && sudo apt-get upgrade

INSTALL CINNAMON
sudo add-apt-repository ppa:embrosyn/cinnamon && sudo apt update && sudo apt install cinnamon

FIX LOGOUT IN CINNAMON
gsettings set org.cinnamon.desktop.session settings-daemon-uses-logind true && gsettings set org.cinnamon.desktop.session session-manager-uses-logind true && gsettings set org.cinnamon.desktop.session screensaver-uses-logind false

INSTALL NUMIX THEME
sudo apt install numix-gtk-theme

REBOOT
sudo reboot

INSTALL GDEBI
sudo apt install gdebi

INSTALL SYNAPTIC
sudo apt install synaptic

INSTALL CHROMIUM
sudo apt install chromium-browser

INSTALL VLC
sudo apt install vlc browser-plugin-vlc

INSTALL SKYPE
Sudo apt install skype

INSTALL DOUBLE COMMANDER
sudo add-apt-repository ppa:alexx2000/doublecmd && sudo apt-get update && sudo apt install ./doublecmd-gtk

INSTALL CHROME
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb

INSTALL VIVALDI
wget https://downloads.vivaldi.com/stable/vivaldi-stable_1.1.453.47-1_amd64.deb
sudo apt install ./vivaldi-stable_1.1.453.47-1_amd64.deb

INSTALL SIMPLENOTE
Download .deb
sudo apt install ./simplenote-1.0.0.deb

INSTALL VIBER
wget -c http://download.cdn.viber.com/cdn/desktop/Linux/viber.deb
sudo apt install ./viber.deb

INSTALL OPERA
Download .deb
sudo apt install ./opera-stable_37.0.2178.32_amd64.deb.deb

INSTALL B1 ARCHIVER
Download .deb
sudo apt install ./b1freearchiver_current_stable_amd64.deb

```

THANKS GUYS FOR ALL YOUR HELP.

---

