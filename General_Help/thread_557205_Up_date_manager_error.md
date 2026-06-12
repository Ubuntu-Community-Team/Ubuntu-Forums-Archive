---
title: "Up date manager error"
date: 2007-09-22
forum: General Help
---

### Post by Matt D on 2007-09-22
The up date manager icon was on the top right hand of the screen so i went to click on it to install the updates and i got this error message 

 E: Type ‘sudo’ is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

How can i fix it

---

### Post by jamvegan on 2007-09-22
The first thing that I would do is look at /etc/apt/sources.list and see if "sudo" is actually there on line 48.  I'm not aware of any reason that it should be in the file anywhere.  If it is, or if anything else doesn't look right to you and you're not sure what it should look like, post the file here and we should be able to help you fix it. :-)

---

### Post by Matt D on 2007-09-25
I think i got the problem when i tried to install beryl from 
[http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)
__________________
and it tells you to edit the software sources

here is my sources list i don't know what should be there
if you can could you get it back to its default 

Thanks Matt 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted main universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

sudo apt-get update
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
sudo gedit /etc/gdm/gdm.conf-custom

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe

---

### Post by jamvegan on 2007-09-25
Okay, the way that that guide is written/formatted is very confusing.  I see why you did what you did (it's what he seems to be telling you to do).  However, you were only meant to add 2 lines to /etc/apt/sources.list:
```
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
```
Then, back at the command line, you're meant to enter the following commands:
```
sudo apt-get update
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
sudo gedit /etc/gdm/gdm.conf-custom
```
the last of which opens /etc/gdm/gdm.conf-custom for editing, where you are meant to add:
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

So, you need to delete the following from your /etc/apt/sources.list:
```
sudo apt-get update
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
sudo gedit /etc/gdm/gdm.conf-custom

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glxbuffer -accel xv:fbo
flexible=true
```
And if you want to completely reverse everything that you did, you would also want to remove the two preceding lines:
```
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
```
In fact, that might be a good idea, since those entries indicate that they are dapper repositories, while the rest of your sources.list indicates that you're running feisty.  Perhaps you can find a newer guide that is relevant to feisty.  (Sorry, I don't know a darn thing about beryl or I'd point you in the right direction.)

Hope this helps!

---

### Post by Matt D on 2007-09-25
Thanks for the help

---

