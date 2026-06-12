---
title: "Package Manager Error"
date: 2008-03-15
forum: General Help
---

### Post by Ressurect on 2008-03-15
Hi, 
I just installed Ubuntu 7.04 and I remembered reading an article about what to do after installing Ubuntu, and so I tried the first step on here:

[http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)

and after doing 'sudo apt-get update' I got this error:

[http://i12.photobucket.com/albums/a243/minisean/Error.png](http://i12.photobucket.com/albums/a243/minisean/Error.png)

Does anyone know how I can rectify this problem or undo it entirely?

---

### Post by forrestcupp on 2008-03-15
Looks like a dated howto.  in a terminal, type:
```
gksu gedit /etc/apt/sources.list
```
and post the contents.

BTW.  Why did you install 7.04 instead of 7.10?

---

### Post by Ressurect on 2008-03-15
> # 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

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
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

I downloaded 7.04 a while ago and burned it onto a CD, and I just used that because I didn't know there was a later version out at the time.

And I think it is a dated how to because I checked the file (in etc/atp/sources.list.d/ called medibuntu.list) and its a XML document.

---

### Post by markharding557 on 2008-03-15
> **Ressurect said:**
> Hi, 
I just installed Ubuntu 7.04 and I remembered reading an article about what to do after installing Ubuntu, and so I tried the first step on here:

[http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)

and after doing 'sudo apt-get update' I got this error:

[http://i12.photobucket.com/albums/a243/minisean/Error.png](http://i12.photobucket.com/albums/a243/minisean/Error.png)

Does anyone know how I can rectify this problem or undo it entirely?

you need to change the medibuntu entry in your sources list to the official one here[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Ressurect on 2008-03-15
Thank you so much, that worked perfectly :)

---

