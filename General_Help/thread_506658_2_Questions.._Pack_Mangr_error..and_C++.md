---
title: "2 Questions.. Pack Mangr error..and C++"
date: 2007-07-22
forum: General Help
---

### Post by computergirl on 2007-07-22
Hi-
Im still "kinda" new to Ubuntu, I Actually LOVE the system. anyhoww, ive been searching the forums trying to find help becasue I cannot get  Synatpic Packager to work. Im looking for C++ compiler, and poof, My packager died out on me.
Here's the error message:

Go to the repository dialog to correct the problem.
E: Type 'sudo' is not known on line 24 in source list /etc/apt/sources.list
E: Unable to lock the list directory

Also, I am a ....ahum....Visual Basic programmer, but learning C++. I would like to know is there is any C++ compilers out there? What about C Im usind DevC++ by Bloodshead now. I dont like using visual studio 2005 - it doesnt run right on my "Other OS" . I love this Unix.Linux system, and was wondering what's avbl, but I cannot find out becasue the package mgr shut me out!

Thank you in advance..

---

### Post by Seisen on 2007-07-22
Post your source list 

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by LuisAugusto on 2007-07-22
> **computergirl said:**
> Hi-
Im still "kinda" new to Ubuntu, I Actually LOVE the system. anyhoww, ive been searching the forums trying to find help becasue I cannot get  Synatpic Packager to work. Im looking for C++ compiler, and poof, My packager died out on me.
Here's the error message:

Go to the repository dialog to correct the problem.
E: Type 'sudo' is not known on line 24 in source list /etc/apt/sources.list
E: Unable to lock the list directory

Also, I am a ....ahum....Visual Basic programmer, but learning C++. I would like to know is there is any C++ compilers out there? What about C Im usind DevC++ by Bloodshead now. I dont like using visual studio 2005 - it doesnt run right on my "Other OS" . I love this Unix.Linux system, and was wondering what's avbl, but I cannot find out becasue the package mgr shut me out!

Thank you in advance..

The error is self explain, you have an mistake on sources.list, you for some weird reason wrote sudo in the line 24 of your sources.list

just:

```
gksu gedit /etc/apt/sources.list
```

Go to line 24 and erase whatever that doesn't follow this standart:

deb(deb-src) something.xxxx.com(org, or whatever) feisty somethinghere

There a various C++ compilers on the repos, however, mono is the only one that work whit Visual Basic (and up tp certain version, I don't remember which, sorry)

---

### Post by computergirl on 2007-07-22
Thanks For the QUICK REPLY! ;-) 
Here's what displayed after I typed in your code:

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes


Now Im still new to all this. Ive only been playing around with it for 8 months now, I usually just use the GUI, not command line. 

Thanks again for helping...

## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.



sudo apt-get update
 apt-get update
 apt-get update
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

---

### Post by Seisen on 2007-07-22
Remove these from your source list

```
sudo apt-get update
apt-get update
apt-get update
```

then everything should work just fine.

---

### Post by computergirl on 2007-07-22
From the command line or from the pkg mgr?
Im in:
    #user@user-desktop:~$
in my terminal window.

Sorry - Like i said Im still new!

Thanks for being patient with me!

---

### Post by computergirl on 2007-07-22
Got IT!  Just as I hit post, I wiped it out of the source.list file. I get it now.....

Its working. TY! ;-)

---

### Post by computergirl on 2007-07-22
Thanks Again!

---

