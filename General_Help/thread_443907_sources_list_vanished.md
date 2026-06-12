---
title: "sources list vanished"
date: 2007-05-14
forum: General Help
---

### Post by DougieFresh4U on 2007-05-14
My  sources list will not open. The following is what I get:
dougie@DougiesToyBox:~$ gksudo gedit /etc/apt/sources.list
dougie@DougiesToyBox:~$ 

Can some one please  help me out?

---

### Post by earobinson on 2007-05-14
here is mine ```
earobinson@minusone:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe #Added by software-properties

# Screenlets
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

## WineHQ - Ubuntu 7.04 "Feisty Fawn"
deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main

# democracy
#deb http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu feisty/
#deb http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu edgy/

```, do things still work?

Also if you post the output when you type ```
history
``` in the terminal we may be able to figure out why.

---

### Post by taurus on 2007-05-14
What's the output of this command from a terminal then?

```
ls -la /etc/apt
```

---

### Post by ep2011 on 2007-05-14
There may be a problem with gksudo or gedit.

Try nano /etc/apt/sources.list

---

### Post by DougieFresh4U on 2007-05-14
Wow!! Thanks for all the quickness. Ok here is what I get: using nano brings up list in terminal,  and taurus, this is what I got with your code:
dougie@DougiesToyBox:~$ ls -la /etc/apt
total 232
drwxr-xr-x   4 root root  4096 2007-05-14 21:10 .
drwxr-xr-x 127 root root 12288 2007-05-14 21:03 ..
drwxr-xr-x   2 root root  4096 2007-05-05 01:11 apt.conf.d
-rw-------   1 root root     0 2007-04-12 06:40 secring.gpg
-rw-r--r--   1 root root  4271 2007-05-14 07:42 sources.list
-rw-r--r--   1 root root  4362 2007-05-11 08:04 sources.list~
-rw-r--r--   1 root root  2684 2007-05-05 01:40 sources.list_backup_200705050140
-rw-r--r--   1 root root  2778 2007-05-06 09:10 sources.list_backup_200705060910
-rw-r--r--   1 root root  2778 2007-05-07 04:31 sources.list_backup_200705070431
-rw-r--r--   1 root root  2778 2007-05-07 05:40 sources.list_backup_200705070540
-rw-r--r--   1 root root  4181 2007-05-14 07:42 sources.list_backup_200705140742
-rw-r--r--   1 root root  4271 2007-05-14 08:48 sources.list_backup_200705140848
drwxr-xr-x   2 root root  4096 2007-03-14 13:44 sources.list.d
-rw-r--r--   1 root root  3737 2007-05-11 07:32 sources.list.save
-rw-------   1 root root  1200 2007-05-11 21:50 trustdb.gpg
-rw-r--r--   1 root root 72490 2007-05-11 21:53 trusted.gpg
-rw-r--r--   1 root root 69900 2007-05-11 21:50 trusted.gpg~

---

### Post by DougieFresh4U on 2007-05-14
**History:**

dougie@DougiesToyBox:~$ history
    1  sudo apt-get update
    2  sudo apt-get dist-upgrade
    3  sudo apt-get -f install
    4  sudo dpkg --configure -a
    5  gksudo gedit /etc/apt/sources.list
    6  sudo apt-get update
    7  sudo apt-get dist-upgrade
    8  sudo apt-get update
    9  sudo apt-get dist-upgrade
   10  sudo apt-get -f install
   11  sudo apt-get install mplayer
   12  sudo apt-get install ffmpeg
   13  gmplayer
   14  gedit ~/.mplayer/gui.conf
   15  sudo apt-get update
   16  sudo apt-get dist-upgrade
   17  sudo nano -Bw /etc/X11/xorg.conf
   18  sudo rm -v /usr/lib/firefox/plugins/libtotem-complex-plugin.*
   19  sudo apt-get remove vlc
   20  sudo apt-get update
   21  sudo apt-get dist-upgrade
   22  sudo apt-get update
   23  sudo apt-get dist-upgrade
   24  sudo apt-get -f install
   25  sudo dpkg --configure -a
   26  sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
   27  wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
   28  sudo apt-get update
   29  sudo apt-get dist-upgrade
   30  sudo apt-get update
   31  sudo apt-get dist-upgrade
   32  gksudo gedit /etc/apt/sources.list
   33  sudo apt-get install ubuntu-restricted-extras
   34  sudo apt-get update
   35  sudo aptitude update
   36  sudo apt-get dist-upgrade
   37  gksudo gedit /etc/apt/sources.list
   38  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
   39  wget -q [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc) -O- | sudo apt-key add -
   40  sudo aptitude update
   41  gksudo gedit /etc/apt/sources.list
   42  sudo apt-get update
   43  gksudo gedit /etc/apt/sources.list
   44  sudo apt-get update
   45  sudo aptitude update
   46  sudo apt-get dist-upgrade
   47  sudo apt-get update
   48  wget [http://debian.cafuego.net/969F3F57.gpg](http://debian.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -
   49  sudo apt-get update
   50  sudo apt-get dist-upgrade
   51  sudo apt-get -f install
   52  sudo aptitude dist-upgrade
   53  sudo apt-get -f install
   54  sudo dpkg --configure -a
   55  sudo apt-get update
   56  wget [http://debian.cafuego.net/969F3F57.gpg](http://debian.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -
   57  sudo apt-get update
   58  sudo wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -
   59  sudo apt-get update
   60  sudo wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -
   61  sudo apt-get update
   62  gksudo gedit /etc/apt/sources.list
   63  sudo apt-get update
   64  sudo apt-get dist-upgrade
   65  sudo apt-get install libdvdcss2 w32codecs
   66  sudo apt-get -f install
   67  sudo apt-get autoremove
   68  exaile
   69  sudo apt-get update
   70  sudo apt-get dist-upgrade
   71  sudo apt-get autoclean
   72  sudo apt-get autoremove
   73  sudo apt-get -f install
   74  sudo dpkg --configure -a
   75  gksudo gedit /etc/X11/xorg.conf
   76  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
   77  sudo apt-get update
   78  sudo apt-get autoremove
   79  sudo apt-get -f install
   80  sudo dpkg --configure -a
   81  sudo apt-get update
   82  sudo apt-get dist-upgrade
   83  amarok
   84  gksudo gedit /etc/apt/sources.list
   85  sudo nano gedit /etc/apt/sources.list
   86  gksudo gedit /etc/apt/sources.list
   87  sudo gedit /etc/apt/sources.list
   88  cat /etc/apt/sources.list
   89  sudo apt-get update
   90  gksudo gedit /etc/apt/sources.list
   91  history

---

### Post by taurus on 2007-05-14
> **DougieFresh4U said:**
> Wow!! Thanks for all the quickness. Ok here is what I get: using nano brings up list in terminal,  and taurus, this is what I got with your code:
dougie@DougiesToyBox:~$ ls -la /etc/apt
total 232
drwxr-xr-x   4 root root  4096 2007-05-14 21:10 .
drwxr-xr-x 127 root root 12288 2007-05-14 21:03 ..
drwxr-xr-x   2 root root  4096 2007-05-05 01:11 apt.conf.d
-rw-------   1 root root     0 2007-04-12 06:40 secring.gpg
**[COLOR="Red"]-rw-r--r--   1 root root  4271 2007-05-14 07:42 sources.list[/COLOR]**
-rw-r--r--   1 root root  4362 2007-05-11 08:04 sources.list~
-rw-r--r--   1 root root  2684 2007-05-05 01:40 sources.list_backup_200705050140
-rw-r--r--   1 root root  2778 2007-05-06 09:10 sources.list_backup_200705060910
-rw-r--r--   1 root root  2778 2007-05-07 04:31 sources.list_backup_200705070431
-rw-r--r--   1 root root  2778 2007-05-07 05:40 sources.list_backup_200705070540
-rw-r--r--   1 root root  4181 2007-05-14 07:42 sources.list_backup_200705140742
-rw-r--r--   1 root root  4271 2007-05-14 08:48 sources.list_backup_200705140848
drwxr-xr-x   2 root root  4096 2007-03-14 13:44 sources.list.d
-rw-r--r--   1 root root  3737 2007-05-11 07:32 sources.list.save
-rw-------   1 root root  1200 2007-05-11 21:50 trustdb.gpg
-rw-r--r--   1 root root 72490 2007-05-11 21:53 trusted.gpg
-rw-r--r--   1 root root 69900 2007-05-11 21:50 trusted.gpg~

There it is.

```
cat /etc/apt/sources.list
```

---

### Post by DougieFresh4U on 2007-05-14
> **taurus said:**
> There it is.

```
cat /etc/apt/sources.list
```

Yes, I see but  I can not edit repos . I can not access through:** gksudo gedit /etc/apt/sources.list. ** And also things are not working. as in none of the music players are working. They open (amarok, exaile) but when I click to play they freeze and I end up doing "Force Quit"
Why do I get this feeling that I shall be trying out one of these nice new cd's I got  in the mail last week from ship-it????

---

### Post by taurus on 2007-05-14
You are running Xubuntu, right?

```
gksudo mousepad /etc/apt/sources.list
```
or
```
sudo nano -Bw /etc/apt/sources.list
```

---

### Post by DougieFresh4U on 2007-05-14
> **taurus said:**
> You are running Xubuntu, right?

```
gksudo mousepad /etc/apt/sources.list
```
or
```
sudo nano -Bw /etc/apt/sources.list
```

Feisty on this one, and I tried the second code and sources came up. How can I get list back to gedit or gksudo?

---

### Post by taurus on 2007-05-14
What's wrong with using nano?  <Ctl>o to save it and <Ctrl>x to exit.

---

### Post by DougieFresh4U on 2007-05-14
> **taurus said:**
> What's wrong with using nano?  <Ctl>o to save it and <Ctrl>x to exit.

Sound fine to me. I was tinkering with enlightment and updates gave me error 404, some thing about  dun repo or some thing like that was not right. Also I just tried Exaile  in terminal and it froze . This is message terminal gave
dougie@DougiesToyBox:~$ exaile
Using multimedia keys from: 'gnome'
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x89a04d0>}
Closed db for thread Thread-1
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/dougie/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 1
Warning: Gstreamer equalizer element not found, please install the latest gst-plugins-bad package
I checked Synaptic and the "bad" set is installed

---

### Post by taurus on 2007-05-14
If you post your /etc/apt/sources.list here, maybe somebody will spot the problem entry for you.

```
cat /etc/apt/sources.list
```

---

### Post by DougieFresh4U on 2007-05-14
> **taurus said:**
> If you post your /etc/apt/sources.list here, maybe somebody will spot the problem entry for you.

```
cat /etc/apt/sources.list
```

Thank you and here it is::

[B]dougie@DougiesToyBox:~$ cat /etc/apt/sources.list
## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
##deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


# Cafuego’s feisty Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)…
deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) feisty-cafuego all
deb-src [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) feisty-cafuego all
## Swiftfox (enhanced Firefox for linux) packages
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free
# syzygy42 repository: avant-window-navigator, exaile, closure… (GPG key: 8434D43A)



#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties
#AUTOMATIX REPOS END[/B]

---

### Post by taurus on 2007-05-14
I am not sure why you even bother to install Automatix since everything you need is already available in the repos!  That sure one way to break your machine.  Exactly what's wrong with your machine?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by DougieFresh4U on 2007-05-14
> **taurus said:**
> I am not sure why you even bother to install Automatix since everything you need is already available in the repos!  That sure one way to break your machine.  Exactly what's wrong with your machine?

```
sudo aptitude update
sudo aptitude upgrade
```

I'm getting this error
[B]Err [http://e17.dunnewind.net](http://e17.dunnewind.net) feisty/e17 Packages                                                                             
  404 Not Found[/B]

 Also, Exaile claims that gstream plugin bad set not installed but Synaptic says it is

---

