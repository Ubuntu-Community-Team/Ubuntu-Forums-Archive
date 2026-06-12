---
title: "Help Me Install Ubuntu GUI"
date: 2013-11-21
forum: General Help
---

### Post by btcinema on 2013-11-21
I have installed Ubuntu 13.10....but only the CORE

I want to install a Gui...but i only get: package not found
When I type: sudo apt-get update I get:

Ign cdrom://Ubuntu-Server 13.10 _Saucy Salamander_ - Release i386 (20131016) saucy InRelease
Ign cdrom://Ubuntu-Server 13.10 _Saucy Salamander_ - Release i386 (20131016) saucy/main Translation-en_US
Ign cdrom://Ubuntu-Server 13.10 _Saucy Salamander_ - Release i386 (20131016) saucy/main Translation-en
Ign cdrom://Ubuntu-Server 13.10 _Saucy Salamander_ - Release i386 (20131016) saucy/restricted Translation-en Us
Ign cdrom://Ubuntu-Server 13.10 _Saucy Salamander_ - Release i386 (20131016) saucy/restricted Translation-en
Reading package lists... Done

That's all... please help me finish the instalation... I dont have gedit...

---

### Post by philinux on 2013-11-21
Do you want to install say a minimum like xfce4 or the full ubuntu-desktop

Have you got networking as it's only seeing cdrom?

---

### Post by btcinema on 2013-11-21
Yes I should have wireless already configured.... I want full ubuntu desktop

---

### Post by philinux on 2013-11-21
> **btcinema said:**
> Yes I should have wireless already configured.... I want full ubuntu desktop

In that case.

```
sudo apt-get install ubuntu-desktop
```

---

### Post by btcinema on 2013-11-21
As I said....there must be a problem somewhere

I get: E: unable to locate package ubuntu-desktop....

---

### Post by philinux on 2013-11-21
> **btcinema said:**
> As I said....there must be a problem somewhere

I get: E: unable to locate package ubuntu-desktop....

```
cat /etc/apt/sources.list
```

Post back the results. Put code tags around it (# key in post editor)

---

### Post by btcinema on 2013-11-21
> deb cdrom:[Ubuntu-Server 13.10 _Saucy Salamander_ - Release i386 (20131016)]/ saucy main restricted
that's all :)

---

### Post by philinux on 2013-11-21
Ok then have you got nano on the system as we need to edit that file.

It should look like this. How did you install what you have?

cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 13.10 Saucy Salamander_ - Alpha amd64 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy universe
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ saucy-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
# deb-src http://extras.ubuntu.com/ubuntu saucy main
```

---

### Post by btcinema on 2013-11-21
is there a wget command ? I don't have nano...and I hate "vi" :)

---

### Post by oldos2er on 2013-11-21
Are you sure you don't have nano? It's installed by default on Ubuntu Server (and desktop too).

---

### Post by btcinema on 2013-11-21
I installed Ubuntu 13.10 using the PC Intel X86 Desktop Image from releases.ubuntu.com
It all went fine until I reached the Install Software (Apache...Tomcat) - An unknown error....

I don't have nano...and I have managed to edit this with VI.... I already hate ubuntu!  spend 4 hours with the instalation...a lot of errors... [Solved] i guess...

---

### Post by philinux on 2013-11-21
> **btcinema said:**
> I don't have nano...and I have managed to edit this with VI.... I already hate ubuntu!  spend 4 hours with the instalation...a lot of errors... [Solved] i guess...

Ok. any reason you didn't go for the full install?

---

### Post by btcinema on 2013-11-21
[COLOR=#000000]I installed Ubuntu 13.10 using the PC Intel X86 Desktop Image from releases.ubuntu.com[/COLOR]
[COLOR=#000000]It all went fine until I reached the Install Software (Apache...Tomcat) - It gave me an unspecified error when I tried to install something....

I downloaded the image saying that it comes with OpenStack Havana... I probably need to install this too so I'll start a new thread if everything goes wrong.

[Solved]
[/COLOR]

---

### Post by oldos2er on 2013-11-21
Hard to tell from what you've told us, but missing both nano and sources.list file sounds like a bad installation, hard disk problems, or something similar. Installing software shouldn't cause those kinds of problems.

Did you md5sum the iso you downloaded, or run the disc integrity check?

---

### Post by btcinema on 2013-11-21
Well..
I really don't know what happend.. It seems that the core is OK...since I managed to modify sources.list and now I have a GUI and other apps...

Thank You!

---

### Post by Zill on 2013-11-21
> **btcinema said:**
> I installed Ubuntu 13.10 using the PC Intel X86 Desktop Image from releases.ubuntu.com...
So you wanted the full desktop version then?  Note that the server version does not have a GUI by default.

> **btcinema said:**
> 
It all went fine until I reached the Install Software (Apache...Tomcat) - An unknown error....
These are server packages that are not, AIUI, installed by default with the desktop version.

Your post [#7]("http://ubuntuforums.org/showthread.php?t=2189229&p=12853848#post12853848") above also implies that you have actually installed the server version:
> deb cdrom:[Ubuntu-[COLOR="#FF0000"]**Server**[/COLOR] 13.10 _Saucy Salamander_ - Release i386 (20131016)]/ saucy main restricted
> **btcinema said:**
> I don't have nano...
Nano *should* be there - it looks like your installation is corrupted.  I suggest you establish exactly which version you want (desktop or server) and then download it again, checking the MD5 sum to ensure the download is correct.  Then burn to a new DVD and re-install.

---

