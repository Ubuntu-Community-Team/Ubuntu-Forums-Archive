---
title: "Must have apps"
date: 2008-05-20
forum: General Help
---

### Post by signseeker on 2008-05-20
I've just done a fresh install of Xubuntu (64bit) - and am just wondering about apps/utilities that are deemed 'must-have' and/or worth installing. 

Any thoughts?

---

### Post by ubuntu27 on 2008-05-20
Well every person has their own killer app or a must have appliaction on their list. Since I don't know your needs or wants, I don't know what to suggest.

So you have done a A FRESH install of Xubuntu. Maybe you wll like to install some restricted codecs?

[Here is the guide:]("https://help.ubuntu.com/community/RestrictedFormats")

in short, input the following command at the Terminal

```
sudo apt-get update && apt-get install xubuntu-restricted-extras
```

You might be interested to read a thread created in this forum called **["Cool applications you use that others might not know ]("http://ubuntuforums.org/showthread.php?t=382137")of"**

It list hundreds of unknown (or not so famous) applications that people like and wants to spread the word.


Oh yes! There is one application that I recommend you to have if you do anything realted to mathematics. [Qalculate! ]("http://qalculate.sourceforge.net/")

[Qalculate!]("http://qalculate.sourceforge.net/") Is a special calculator that lets you input functuions, it allows you to convert units, convert monetary currency, etc.

It is in the repositories.

---

### Post by shifty_powers on 2008-05-20
heh, well i do like awn, got used to having a dock bar. just type awn into synaptic ;)

edit: adn you can get those restricted extras by simply going to applications> add/remove as well ;)

you'll find some cool stuff in there :D

---

### Post by NightwishFan on 2008-05-20
Hardinfo: System Information
Xfmedia: Media Player
Vlc: Speaks for itself
Mousepad: Text editor
Xfburn: If you hate brasero
Frozen Bubble: Fun game
Deluge-Torrent - Bittorrent Client
Kazehakase - Web Browser

---

### Post by ibuclaw on 2008-05-20
> **NightwishFan said:**
> Hardinfo: System Information
Xfmedia: Media Player
Vlc: Speaks for itself
Mousepad: Text editor
Xfburn: If you hate brasero
Frozen Bubble: Fun game
Deluge-Torrent - Bittorrent Client
Kazehakase - Web Browser

"cat /proc/* > ~/hardinfo.log": Hardware Information...
totem-xine: Media Player
vlc-nox: Must have! :D
emacs22-nox: Text Editor (Although, Leafpad is a good tool too for you GUI users)
NeroLinux3: If you hate Xfburn :p
[Phun]("http://phun.cs.umu.se/wiki"): "Phun" Game...
KTorrent: Bit Torrent
FireFox: Web Browser

---

### Post by justin whitaker on 2008-05-20
Must Haves:
Restricted Extras
MS Core Fonts
Libdvdcss2 (or so I am told...:))
MPlayer
VLC
Thunderbird
Inkscape
Midnight Commander

---

### Post by ibuclaw on 2008-05-20
> **justin whitaker said:**
> 
Libdvdcss2 (or so I am told...:))


Actually, its the following list together that makes it work:
[LIST]
[*]libdvd0
[*]libdvdcss2
[*]libdvdnav4
[*]libdvdplay0
[*]libdvdread3
[/LIST]
Then install totem-xine (plus some other plugins), and you are all set.
At least, I have much better DVD Menu playblack with Xine than whatever GSTreamer could ever give...

Regards
Iain

---

### Post by signseeker on 2008-05-20
> **shifty_powers said:**
> heh, well i do like awn, got used to having a dock bar. just type awn into synaptic ;)

edit: adn you can get those restricted extras by simply going to applications> add/remove as well ;)

you'll find some cool stuff in there :D

I used awn with gentoo and xfce but I used to get a weird screen redraw problem. Also there was a slow but irritating memory leak. I will definitely try it again with Xubuntu though. Thanks for reminding me.

---

### Post by Cifra on 2008-05-20
Wrote a post about this on my blog not long ago: [http://www.internetling.com/2008/05/10/top-ten-apps-i-install-immediately-after-the-ubuntu-linux-setup/](http://www.internetling.com/2008/05/10/top-ten-apps-i-install-immediately-after-the-ubuntu-linux-setup/)

---

### Post by digisoft on 2008-05-20
I tried that to get the restricted extras and got an error
[PHP]
rocks@lilbit:~$ sudo apt-get update && apt-get install xubuntu-restricted-extras
[sudo] password for rocks: 
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://archive.canonical.com hardy Release.gpg                   
Ign http://archive.canonical.com hardy/partner Translation-en_US     
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://archive.canonical.com hardy Release 
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy/main Packages                 
Hit http://us.archive.ubuntu.com hardy/restricted Packages           
Hit http://us.archive.ubuntu.com hardy/main Sources                  
Hit http://us.archive.ubuntu.com hardy/restricted Sources            
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://archive.canonical.com hardy/partner Sources               
Hit http://us.archive.ubuntu.com hardy/universe Packages             
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
rocks@lilbit:~$ [/PHP]


I know for a fact I was using the root password, so why did I get this? I went into synaptics package manager and did a search for "xubuntu-restricted-extras" and found one file, I installed it with no problem from there. Is that the same as I would have got from doing it the other way?

---

