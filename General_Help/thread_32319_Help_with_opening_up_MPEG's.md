---
title: "Help with opening up MPEG's"
date: 2005-05-07
forum: General Help
---

### Post by JC4P on 2005-05-07
Ok so i tried to open up MPEG's and couldnt. and read some other threads. and they all told me to go with either MPlayer, Kplayer, Totem-Xine. and so on. Each one i try to download, i get errors. watch i get for MPlayer:
> The following packages have unmet dependencies:
  mplayer-386: Depends: libartsc0 (>= 1.3.2) but it is not going to be installed               Depends: libasound2 (> 1.0.8) but 1.0.5-1ubuntu1 is to be installed
               Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libbio2jack0 but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-13ubuntu2 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.2-2ubuntu3 is to be installed
               Depends: libggi2 (>= 1:2.0.5) but it is not going to be installed               Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
               Depends: libjack0.80.0-0 (>= 0.99.0) but it is not going to be installed
               Depends: libogg0 (>= 1.1.2) but 1.1.0-1 is to be installed
               Depends: libpng12-0 (>= 1.2.8rel) but 1.2.5.0-7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libsdl1.2debian (> 1.2.7+1.2.8) but 1.2.7-7 is to be installed
               Depends: libungif4g (>= 4.1.3) but 4.1.0b1-6 is to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but it is not going to be installed
E: Broken packages


and for Kplayer:
> The following packages have unmet dependencies:
  kplayer: Depends: kdelibs4 (>= 4:3.3.2-2) but it is not going to be installed
           Depends: libidn11 (>= 0.5.2) but 0.4.1-1 is to be installed
           Depends: libpng12-0 (>= 1.2.8rel) but 1.2.5.0-7 is to be installed
           Depends: libqt3c102-mt (>= 3:3.3.3) but it is not going to be installed
           Depends: mplayer
E: Broken packages


can anyone help? also when i tried to get Totem-Xine it deleted the other one and now i dont have totem at all. and when i Try to install the other Totem again i need to put in  the Ubuntu CD again but i gotta burn another copy of that.

---

### Post by kvidell on 2005-05-07
[QUOTE=JC4P]also when i tried to get Totem-Xine it deleted the other one and now i dont have totem at all. and when i Try to install the other Totem again i need to put in  the Ubuntu CD again but i gotta burn another copy of that.[/QUOTE]
 I'd say remove the CDs from your apt source list, add the special repositories, update, and try totem again.
It should work just fine.
- Kev

---

### Post by JC4P on 2005-05-07
[QUOTE=kvidell]I'd say remove the CDs from your apt source list, add the special repositories, update, and try totem again.
It should work just fine.
- Kev[/QUOTE]
 well i had Totem Before and when i double clicked on a MPG file it just froze up.

---

### Post by kvidell on 2005-05-07
[QUOTE=JC4P]well i had Totem Before and when i double clicked on a MPG file it just froze up.[/QUOTE]
 Well that's pretty unproductive then isn't it?
try the follow faq yet?
[http://www.ubuntuforums.org/showthread.php?t=31061](http://www.ubuntuforums.org/showthread.php?t=31061)
- Kev

---

### Post by JC4P on 2005-05-07
[QUOTE=kvidell]Well that's pretty unproductive then isn't it?
try the follow faq yet?
[http://www.ubuntuforums.org/showthread.php?t=31061](http://www.ubuntuforums.org/showthread.php?t=31061)
- Kev[/QUOTE]
 tried it got the error Mplayer that i put in first post (first quotebox)

---

### Post by kvidell on 2005-05-07
[QUOTE=JC4P]tried it got the error Mplayer that i put in first post (first quotebox)[/QUOTE]
 sudo apt-get install -t hoary mplayer-586 mplayer-fonts
is what ended up being the only thing that worked for me.
(requires multiverse)
That was a little farther down in that faq.

---

### Post by JC4P on 2005-05-07
[QUOTE=kvidell]sudo apt-get install -t hoary mplayer-586 mplayer-fonts
is what ended up being the only thing that worked for me.
(requires multiverse)
That was a little farther down in that faq.[/QUOTE]
 multiverse?

---

### Post by kvidell on 2005-05-07
[QUOTE=JC4P]multiverse?[/QUOTE]
 Aye.
The multiverse repositores in your /etc/apt/sources.list file.
ie:
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Where mine says "universe" "main" or "restricted", you could also add the word "multiverse" to gain access to those repositories.

Add the word to the line, run apt-get update, then try again.

Please note: Do not copy my sources.list and add multiverse options, it's configured for the unstable release of Ubuntu (breezy) :-P You'd find yourself in a rather strange place if you did so and weren't expecting it.

- Kev

---

### Post by bored2k on 2005-05-07
[QUOTE=JC4P]multiverse?[/QUOTE]
 Yes, enable it with
```
sudo echo deb http://archive.ubuntu.com/ubuntu hoary multiverse >> /etc/apt/sources.list && sudo echo deb-src http://archive.ubuntu.com/ubuntu hoary multiverse >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get install -t hoary mplayer-586 mplayer-fonts && echo "That's that, you could also try installing vlc-esd"
```

---

### Post by JC4P on 2005-05-07
[QUOTE=kvidell]Aye.
The multiverse repositores in your /etc/apt/sources.list file.
ie:

Where mine says "universe" "main" or "restricted", you could also add the word "multiverse" to gain access to those repositories.

Add the word to the line, run apt-get update, then try again.

Please note: Do not copy my sources.list and add multiverse options, it's configured for the unstable release of Ubuntu (breezy) :-P You'd find yourself in a rather strange place if you did so and weren't expecting it.

- Kev[/QUOTE]
 I'm at the ./configure --enable-gui stage of complieing MPlayer. And i get this: Error: The GUI requires GTK devel packages (which were not found).

Check "configure.log" if you do not understand why it failed.

---

### Post by bored2k on 2005-05-07
[QUOTE=JC4P]I'm at the ./configure --enable-gui stage of complieing MPlayer. And i get this: Error: The GUI requires GTK devel packages (which were not found).

Check "configure.log" if you do not understand why it failed.[/QUOTE]
 ```
sudo echo deb http://archive.ubuntu.com/ubuntu hoary multiverse >> /etc/apt/sources.list && sudo echo deb-src http://archive.ubuntu.com/ubuntu hoary multiverse >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get install -t hoary mplayer-586 mplayer-fonts && echo "That's that, you could also try installing vlc-esd"
```

Use your super-cow debian powers..

---

### Post by JC4P on 2005-05-07
[QUOTE=bored2k]```
sudo echo deb http://archive.ubuntu.com/ubuntu hoary multiverse >> /etc/apt/sources.list && sudo echo deb-src http://archive.ubuntu.com/ubuntu hoary multiverse >> /etc/apt/sources.list && sudo apt-get update && sudo apt-get install -t hoary mplayer-586 mplayer-fonts && echo "That's that, you could also try installing vlc-esd"
```

Use your super-cow debian powers..[/QUOTE]
 used my superawesome powers that i picked up using Linspire and Matrix The GAme to se that code. and all i got was this: > The following packages have unmet dependencies:
  mplayer-586: Depends: libartsc0 (>= 1.3.2) but it is not going to be installed               Depends: libasound2 (> 1.0.8) but 1.0.5-1ubuntu1 is to be installed
               Depends: libfribidi0 (>= 0.10.4-5) but 0.10.4-3 is to be installed
               Depends: libgcc1 (>= 1:4.0-0pre6ubuntu4) but 1:3.4.2-2ubuntu1 is to be installed
               Depends: libggi2 (>= 1:2.0.5) but it is not going to be installed               Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
               Depends: libogg0 (>= 1.1.2) but 1.1.0-1 is to be installed
               Depends: libpng12-0 (>= 1.2.8rel) but 1.2.5.0-7 is to be installed
               Depends: libsdl1.2debian (> 1.2.7+1.2.8) but 1.2.7-7 is to be installed
               Depends: libungif4g (>= 4.1.3) but 4.1.0b1-6 is to be installed
               Depends: libxinerama1 but it is not installable
               Depends: libxxf86dga1 but it is not installable
               Depends: libxxf86vm1 but it is not installable
E: Broken packages


---

### Post by JC4P on 2005-05-07
[QUOTE=JC4P]used my superawesome powers that i picked up using Linspire and Matrix The GAme to se that code. and all i got was this:[/QUOTE]
 any one else try out to help?

---

### Post by bored2k on 2005-05-07
What's in your /etc/apt/sources.list ?
Make sure ubuntu repositories are the only ones being used.

---

### Post by JC4P on 2005-05-07
[QUOTE=bored2k]What's in your /etc/apt/sources.list ?
Make sure ubuntu repositories are the only ones being used.[/QUOTE]
 here it is:
[QUOTE]deb cdrom:Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main multiverse 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary multiverse 
## deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary multiverse 

## deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main multiverse
## deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main multiverse 

## deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
## deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

## deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
## deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
[\QUOTE]

---

