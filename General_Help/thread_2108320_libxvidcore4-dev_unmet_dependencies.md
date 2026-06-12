---
title: "libxvidcore4-dev unmet dependencies"
date: 2013-01-24
forum: General Help
---

### Post by qwikrazor87 on 2013-01-24
Hello everyone.
I am having some trouble trying to install libxvidcore4-dev.
Here is the error message I am getting:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libxvidcore4-dev : Depends: libxvidcore4 (= 2:1.2.2-0.1) but 2:1.3.2-6 is to be installed
E: Unable to correct problems, you have held broken packages.
```I tried sudo apt-get clean and auto clean, removed and reinstalled libxvidcore4 but the error still occurs.

I am trying to install that package so I can install PSPVC to convert videos for my PSP.

Here is the info from cat /etc/apt/sources.list:
```
# deb cdrom:[Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://www.deb-multimedia.org squeeze main
```Here is the info from cat /etc/apt/sources.list.d/*:
```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
```
I'd appreciate if someone can help me solve this problem. Thanks.

---

### Post by furything on 2013-01-24
Try this thread to force removal of packages

[http://ubuntuforums.org/showthread.php?t=947124&page=3](http://ubuntuforums.org/showthread.php?t=947124&page=3)

or
```
sudo apt-get install -f
```
To force repair of packages

---

### Post by qwikrazor87 on 2013-01-24
Hello furything, thanks for your reply.
I forgot to mention that I tried that too. The problem still occurs. I tried out the solutions on the thread you linked but it still does not help.

I tried 
sudo dpkg --remove -force --force-remove-reinstreq libxvidcore4-dev and here's what I got:
```
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by mc4man on 2013-01-24
The name has changed, it's now libxvidcore-dev

So may be easiest to remove libxvidcore4, update your sources, then install libxvidcore-dev, libxvidcore4

(if you install & use synaptic it's quite easy to see & do.

---

### Post by qwikrazor87 on 2013-01-24
Thank you mc4man, that has cleared the problem with installing that package.
Now I am having a problem installing PSPVC.
I ran sudo sh install.sh and got this:
```
ERROR: x264 not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-devel@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.
-e \E[01;31mERROR during configure FFMPEG
```
I have x264 installed and it is the latest version. I also installed yasm, ffmpeg and all the necessary libraries for PSPVC but the problems still occur.
Thank you for your help.

---

### Post by mc4man on 2013-01-24
> **qwikrazor87 said:**
> Thank you mc4man, that has cleared the problem with installing that package.
Now I am having a problem installing PSPVC.
I ran sudo sh install.sh and got this:
```
ERROR: x264 not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-devel@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.
-e \E[01;31mERROR during configure FFMPEG
```
I have x264 installed and it is the latest version. I also installed yasm, ffmpeg and all the necessary libraries for PSPVC but the problems still occur.
Thank you for your help.

Don't know what PSPVC is & atm am not going to look into. It does appear that your install.sh is going to build (or try to) PSPVC or ffmpeg??, if that's the case then try installing this if not already
libx264-dev

(if already installed then could be a x264 version issue, if inclined post a link to PSPVC source

---

### Post by qwikrazor87 on 2013-01-24
> **mc4man said:**
> Don't know what PSPVC is & atm am not going to look into. It does appear that your install.sh is going to build (or try to) PSPVC or ffmpeg??, if that's the case then try installing this if not already
libx264-dev

(if already installed then could be a x264 version issue, if inclined post a link to PSPVC source
PSPVC is a video conversion program.
Yes I also installed libx264-dev, still no change with the error.

Here is the source for the app I'm trying to compile,
[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)
Thanks.

---

### Post by mc4man on 2013-01-24
Well that source is 5+ years old & is/was using just as ancient x264 & ffmpeg sources.

You could likely force it to use the included x264/ffmpeg sources & install all to a dir. in /opt but then you'd likely need to either install a much older gcc & export it in the build script or fix all the probable compiler errors.
Seems like a waste of time...

---

### Post by qwikrazor87 on 2013-01-24
Thanks mc4man.
Yeah that is too much hassle to deal with. I'll just use an online converter, slower but it still works.
Thanks for your time.

---

