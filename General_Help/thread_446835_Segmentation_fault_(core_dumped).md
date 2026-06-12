---
title: "Segmentation fault (core dumped)"
date: 2007-05-17
forum: General Help
---

### Post by Carwyn on 2007-05-17
Using Ubuntu Feisty.

Every time I try and "sudo aptitude" all I get is this; "Segmentation fault (core dumped)".

I had it before, and today I reinstalled Ubuntu, wiping everything except my /home as that had all my mdeia files on it that I don't want to lose.

Here is a run down of what happened when the error started happening (again):

```
carwyn@Yuri:~$ sudo pon dsl-providerPassword:Plugin rp-pppoe.so loaded.carwyn@Yuri:~$ sudo gedit /etc/X11/xorg.conf
carwyn@Yuri:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
OK
carwyn@Yuri:~$ sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
--00:11:29--  http://medibuntu.sos-sts.com/sources.list.d/feisty.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125, 88.191.13.100, 88.191.26.58, ...
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 240 [text/plain]

100%[====================================>] 240           --.--K/s             

00:11:30 (18.78 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [240/240]
carwyn@Yuri:~$ sudo apt-get update
Get:1 http://cn.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://cn.archive.ubuntu.com feisty/main Translation-en_US  

[lots of packet information]

Reading package lists... Done
carwyn@Yuri:~$ sudo aptitude install w32codecs
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install w32codecs
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install libxine-extracodecs xine-ui mplayer mplayer-skins vlc vlc-plugin-*
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install xmms xmms-mad xmms-skins xmms-wma mpg123 banshee amarok
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install libxine-extracodecs xine-ui
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude install flashplugin-nonfree
Segmentation fault (core dumped)
carwyn@Yuri:~$ sudo aptitude
Segmentation fault (core dumped)

```

Any help would be appreciated. I have already formatted my '/' drive today, and 'swap', just not my '/home' as that's where all my important stuff is stored. And it seems that alot of my basic settings have been carried over from before, things like wallpapers, deleting speed on typing etc.

---

### Post by taurus on 2007-05-17
If you don't mount your /home, then how are you going to log in since there is no /home/**username**?

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Carwyn on 2007-05-17
This is what i got:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://cn.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cn.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://cn.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cn.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cn.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse

```
And my home is mounted, I just haven't formatted it.

---

### Post by kmcc049 on 2008-01-21
ok hating to flog a dead horse here but today I found myself with a similar error in my mythbuntu installation.  I did an 

```
apt-get update 
```

followed with an 

```
apt-get upgrade
```

for whatever reason, maybe it had being to long and there were two many updates or maybe mythtv was trying to to agressively restart things I dont know I had two packages fail to install 
libmyth-0.20_0.20.2+fixes15422-0ubuntu0~mythbuntu1_i386.deb
and
mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb

so I ran
```
apt-get upgrade
```

again and it failed with a segmentation fault after sitting at reading package lists for ages and locking the system.  So I tried again, same thing.  Forced an fsck on reboot and tried after that same thing again.  Tried it with aptitude and got another similar error.   Tried deleting the .deb files and retrying still an error.  Tried throwing things and yelling.... didnt help.  So i thought I'd try and reinstall apt-get coludn't figure out how, but looked more indepth at dpkg, I redownloaded the files into /var/cache/apt/archives and did a 

```

dpkg -i /var/cache/apt/archives/mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb
dpkg -i /var/cache/apt/archives/libmyth-0.20_0.20.2+fixes15422-0ubuntu0~mythbuntu1_i386.deb

```

and they both installed :).  Not only that but a subsequent apt-get upgrade worked fine :) :) :) :) :)
and now things seem to be ok.  I hope that this helps someone in the future which is why i am posting this as I didnt find what i did suggested anywhere.

---

