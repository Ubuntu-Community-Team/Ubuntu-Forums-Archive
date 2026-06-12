---
title: "apt-get does nothing?"
date: 2005-06-24
forum: General Help
---

### Post by Garyu on 2005-06-24
Well, I've done all I can, to no avail, so I hope someone here will be able to help me out a bit. 

I have read the Ubuntu 5.04 Starter Guide (ubuntuguide.org) and added the extra repositories they mention, and yet apt-get finds nothing for me when I am trying to install software. Synaptic, however, works fine and it has a list of all the repositories I added using the help at ubuntuguide.org. BUT the software I want is (among other things) NVU web editor, which Synaptic cannot find. *boohoo*

The error message I get is:
root@minotaur:/home/danerik # apt-get install nvu
Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
E: Kunde inte hitta paketet nvu

(I use su rather than sudo, the result is the same)
(oh, hehe, the message is in swedish - it says "E: could not find package nvu")

I get the same message no matter what package I try to install. So... what to do?

---

### Post by rmjokers on 2005-06-24
Have you tried to run:

sudo apt-get update
apt-cache search ?package?

before you try to install the software named ?package?

It doesnt look like nvu is in the ubuntu repositories, at least the ones I am subscribed to.  However, you could download the .deb package from the nvu website and use dpkg to install it.

---

### Post by Garyu on 2005-06-24
well, apt-cache returns nothing, as expected since the error I get is that the package cannot be found...

BUT the ubuntuguide.org says that I should use apt-get to install both nvu and for example realplayer and mozilla-plugins. Quite frustrating to have a guide tell you one thing and experiencing that it does not work (though they made a GREAT guide in other respects).

Anywayz, I guess I'll be forced to try to learn how to install a debian package... 

I really love ubuntu (I've tried mandrake 10.1 and SuSE 9.2 before, and encountered nothing but problems). In ubunty most things work, and they work well. The only problems I have encountered are in multimedia and in installing software as mentioned. I still haven't been able to fix 5.1 surround sound. But I doubt I will ever use another distro as long as ubuntu is this stable and functioning. =)

---

### Post by Xian on 2005-06-24
[QUOTE=Garyu]well, apt-cache returns nothing, as expected since the error I get is that the package cannot be found...[/QUOTE]
NVU is in the backports repo.
Do you have something similar to this in your /etc/apt/sources.list?
```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
Here is my apt session:
```
sudo apt-get install nvu
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  nvu
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 8607kB of archives.
After unpacking 25.7MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  nvu
Install these packages without verification [y/N]?
```

---

### Post by jengo on 2005-06-24
I get the same problem! should I change my Sources.list to have those backports you mentioned? if so, let me try again.

---

### Post by Xian on 2005-06-24
[QUOTE=jengo]I get the same problem! should I change my Sources.list to have those backports you mentioned? if so, let me try again.[/QUOTE]
Yes, if you don't have the backports listed then add the repos provided below to the end of your /etc/apt/sources.list file. Add them just as written.

```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
Then open Synaptic and hit the 'Reload' button, or use this command in a terminal:
```
$ sudo apt-get update
```

---

### Post by jengo on 2005-06-24
okay I added them and did the sudo update thing and got this:

> root@diegoscomputer:/home/diego # sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
99% [Connecting to ubuntu-backports.mirrormax.net] 

is there something Im doing wrong? cause this thing is taking forever. and as you see above there are errors, and what does ign mean?

---

### Post by cutOff on 2005-06-24
Try to use this backports repositories instead of other ones

```
##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
```

---

### Post by Xian on 2005-06-24
[QUOTE=jengo]is there something Im doing wrong? cause this thing is taking forever. and as you see above there are errors, and what does ign mean?[/QUOTE]
Yeah, it appears to be a server issue.
Do as cutOff correctly suggested and try the update command again.

---

### Post by jengo on 2005-06-24
Sweet! its working pretty good so far! Thanks cutoff! Your a champ!

---

### Post by jengo on 2005-06-24
woot! im finally going to get everything that I wanted working, Working! w00t.

---

### Post by Garyu on 2005-07-01
[QUOTE=Xian]NVU is in the backports repo.
Do you have something similar to this in your /etc/apt/sources.list?
```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
[/code][/QUOTE]

Hey Xian,

Thanks a lot for trying to help, but you did not do much. I have added the repositories you mention (mirrormax) and they still return "package not found".

HOWEVER, I might have realized why. I'm running the 64-bit kernel, so I'm guessing that there just isn't a 64-bit version of nvu out there. 

Since the source-compile-instructions at [www.nvu.com](www.nvu.com) seemed kind of complex to do for a noob like me I tried downloading the Linspire-tar. It expands to a directory with a nvu-executable, but even though the program starts it self-terminates when I try to do anything. So I found an older version of nvu as a .deb-package, but when I run dpkg-i nvu_0.99... it tells me that I need newer versions of libc6 and libfontconfig1, BUT apt-get tells me I have the newest versions... *sigh*

Ubuntu is great, but user-friendly? No way... Not when it comes to adding functionality. But I guess that comes with the Linux territory...

---

