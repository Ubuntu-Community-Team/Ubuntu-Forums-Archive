---
title: "Megasync Dependency is not satifiable"
date: 2017-02-18
forum: General Help
---

### Post by cobras on 2017-02-18
Greetings Benevolent Gurus;

I've had a look around and can't find an answer applicalbe to my specs, so I hope you can help.

I'm running Ubunut 12.04 on a Toshiba Satellite C55-A upgraded to 12GB RAM.  I need to upgrade Ubuntu and thought I should back up my most precious folders and files.  For this I looked to Mega, but when I go to download Megasync I get the old "Dependency is not satisfiable: libcrypto++9".  I've found instructions for similar issues but for other flavors of Ubuntu and don't want to just start taking shots in the dark.

Ubuntu 12.04 has been a challenge since I installed it, and it's going to be a challenge to uninstall.  Sorry PP, but I'll be glad to see you go.

By the way, when I go to check if my Title has already been posted, I'm denied permission.  I wonder if  this is yet another of PP's endearing traits.

---

### Post by howefield on 2017-02-18
Well, to start off, Ubuntu 12.04 has a few months left of its support cycle so it is right to upgrade.

The package libcrypto++9 should be available in 12.04, it is in the Universe repository, do you have it enabled ?

What's the output of the terminal command..

```
apt-cache policy  libcrypto++9
```

---

### Post by cobras on 2017-02-18
So I should upgrade to 12.04 first?

Output follows:

libcrypto++9:
  Installed: (none)
  Candidate: (none)
  Version table:

Thank you.

---

### Post by howefield on 2017-02-18
> **cobras said:**
> So I should upgrade to 12.04 first?

Reading your first post I thought you were already on 12.04, is that not correct ?

Open the Software & Updates application (might be called something else in 12.04, eg Software Sources) and ensure a check against the universe repository.

Then do a 

```
sudo apt update
```

from the terminal, does that return anything from ```
apt-cache policy  libcrypto++9
```

---

### Post by cobras on 2017-02-18
I'm sorry, you're right.  It's 12.04.

I do the update regularly - the apt-get update anyway.  What's the difference?

Anyway, I did as you suggested, and got the same results.

The closest I could find for the for the universe repository in _Software & Updates_:

**Community-maintained free and open-source software (universe)**, which is ticked off.

---

### Post by DuckHook on 2017-02-18
> **howefield said:**
> …The package libcrypto++9… is in the Universe repository, do you have it enabled ?

> **cobras said:**
> …I do the update regularly - the apt-get update anyway.  What's the difference?
@cobras

As howefield has stated, you need the "universe" repository enabled, else you won't have access to this file irrespective of updating. To see if it is enabled, please post output of:```
cat /etc/apt/sources.list | grep -i universe
```There should be ***no*** hash marks (#) in front of any of the "deb http://-------" lines except possibly the cdrom one.

You can enable the universe repository through the Dash&#8594;Update Manager&#8594;Settings&#8594;Ubuntu Software&#8594;"Community-maintained free and open-source software" (universe).  Make sure this box is checked.

Only then do the whole:```
apt-get update
apt-cache policy libcrypto++9
```…business.

---

### Post by cobras on 2017-02-18
```
@cobras:~$ cat /etc/apt/sources.list | grep -i universe
## team. Also, please note that software in universe WILL NOT receive any
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
```

Something about that just doesn't look right.  Either something got truncated or inadvertently inserted.

...or the file is corrupt?

---

### Post by DuckHook on 2017-02-18
It is clear that you don't have a standard install. Your sources.list file is used to point apt to the right repos. But yours is pointed to the Xenial repos whereas you've told us that you are still on Precise. There is a big mismatch here and you won't be able to safely proceed further with your current setup.

Here's what I suggest: rather than using a third-party backup that calls for the installation of libraries, use the existing software that's already part of your OS. You can simply rsync to your backup media and have an exact copy of the data that you want to keep. There's no compressed or other oddball file format that you would have to deal with, so in the final analysis, you could just drag and drop the files back from your backup if need be.

Then, do a virgin install. Don't try to upgrade, which seems to be at the root of your problems.

---

### Post by howefield on 2017-02-18
To be honest, I'd be interested in what the system thinks it is rather than you telling us.

What's the output of 

```
cat /etc/*-release
```
and
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by cobras on 2017-02-18
Any suggestions on backing up my Gimp library?  Gimp is one of the apps that has not worked right all this time, but I still need that library.

---

### Post by DuckHook on 2017-02-18
Gimp libraries would be located in your /home directory just like all user data. I would simply rsync my whole /home directory and deal with finding the data later. Much safer that way. Also, howefield is spot-on. It may be that you are already running Xenial and not on Precise at all.

But your system is definitely not in a default state. The universe repos are turned on in a default install.

I'm stepping out for now. You are in good hands with howefield. Please post what he asks.

---

### Post by cobras on 2017-02-18
```
@cobras:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
NAME="Ubuntu"
VERSION="16.04.2 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.2 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial
```

I SWEAR TO GOD I DON'T KNOW WHERE THAT CAME FROM.  I never upgraded.

---

### Post by howefield on 2017-02-18
> **cobras said:**
> I never upgraded.

Sure you didn't, it either jumped from the disk itself or you installed it, I know where my money is. 

So you'll be able to use the 16.04 Mega package which will have the correct dependencies for your version.

```
Depends: libc-ares2 (>= 1.7.4), libc6 (>= 2.16), **libcrypto++9v5**, libgcc1 (>= 1:3.0), libqt4-dbus (>= 4:4.5.3), libqt4-network (>= 4:4.7.0~beta1),
libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.8.0), libsqlite3-0 (>= 3.5.9), libssl1.0.0 (>= 1.0.2~beta3), libstdc++6 (>= 5.2), apt-transport-https
```

---

### Post by cobras on 2017-02-18
> **howefield said:**
> Sure you didn't, it either jumped from the disk itself or you installed it, I know where my money is. 


Is it inconceivable that, for example, some rogue program is out there flipping OS versions on unsuspecting patsies such as myself?

I've tried copy/paste and entering the code by hand but keep getting ```
bash: syntax error near unexpected token `>'
```

---

### Post by howefield on 2017-02-19
> **cobras said:**
> Is it inconceivable that, for example, some rogue program is out there flipping OS versions on unsuspecting patsies such as myself?

I've tried copy/paste and entering the code by hand but keep getting ```
bash: syntax error near unexpected token `>'
```

Well, think about it, first you say you have 12.04, then you say you don't, then you say you do, then it turns out you have 16.04. You are asked questions to clarify then you veer off in another direction instead of answering them. Is it conceivable that you are simply confused and that is more probable than a "rogue program" ?

Exactly what "code" did you try to enter ?

---

### Post by cobras on 2017-02-19
> **howefield said:**
> ...

Sorry for that weak attempt at humor.

Thank you for your help, and pardon me for taking your time.

---

