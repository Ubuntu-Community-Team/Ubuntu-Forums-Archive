---
title: "Where is liblame0?"
date: 2005-05-18
forum: General Help
---

### Post by Nick Post on 2005-05-18
I've got all the common resources.  But liblame0 isn't around.  ???

What repository to add?

Here's mine currently:

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

# From the Ubuntu howcome page, these are the backport repositories, like
# for mp3 decoders and other greyware
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

# From the breakmyUbuntu (so, risky eh) page
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main
deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free

Ok, there is a liblame0 on cerkinfo.be but it's not  3.96.1-1 it's  3.96.1-0sarge1,

Edited to add:
Here's a little of what I'm seeing now, acutally.

> mark@postagulous:~$ sudo apt-get install liblame0 Password:
Reading package lists... Done
Building dependency tree... Done
liblame0 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gstreamer0.8-lame: Depends: liblame0 (>= 3.96.1-1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mark@postagulous:~$ sudo apt-get -f install liblame0
Reading package lists... Done
Building dependency tree... Done
liblame0 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gstreamer0.8-lame: Depends: liblame0 (>= 3.96.1-1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mark@postagulous:~$

Edited again to add my latest attempt:

> mark@postagulous:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gstreamer0.8-lame libmp3lame0
The following packages will be REMOVED:
  liblame0
The following NEW packages will be installed:
  libmp3lame0
The following packages will be upgraded:
  gstreamer0.8-lame
1 upgraded, 1 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/327kB of archives.
After unpacking 53.2kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  gstreamer0.8-lame libmp3lame0
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 66619 files and directories currently installed.)
Preparing to replace gstreamer0.8-lame 0.8.8-0.1 (using .../gstreamer0.8-lame_0.8.8.2_i386.deb) ...
Unpacking replacement gstreamer0.8-lame ...
(Reading database ... 66619 files and directories currently installed.)
Removing liblame0 ...
Selecting previously deselected package libmp3lame0.
(Reading database ... 66613 files and directories currently installed.)
Unpacking libmp3lame0 (from .../libmp3lame0_3.96.1-0.2_i386.deb) ...
Setting up libmp3lame0 (3.96.1-0.2) ...

Setting up gstreamer0.8-lame (0.8.8.2) ...

mark@postagulous:~$ sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb
dpkg - warning: downgrading gstreamer0.8-lame from 0.8.8.2 to 0.8.8-0.1.
(Reading database ... 66620 files and directories currently installed.)
Preparing to replace gstreamer0.8-lame 0.8.8.2 (using gstreamer0.8-lame_0.8.8-0.1_i386.deb) ...
Unpacking replacement gstreamer0.8-lame ...
dpkg: dependency problems prevent configuration of gstreamer0.8-lame:
 gstreamer0.8-lame depends on liblame0 (>= 3.96.1-1); however:
  Package liblame0 is not installed.
dpkg: error processing gstreamer0.8-lame (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gstreamer0.8-lame

---

### Post by defkewl on 2005-05-19
Try adding debian repositories.

---

### Post by az on 2005-05-19
[QUOTE=defkewl]Try adding debian repositories.[/QUOTE]
No.  Do not do that.

The problem is that you have backports which are screwing up your dependancies.  If you want to solve the problem by using a debian package from sid, try installing it by hand.  You may be able to get away with it since it is only one package.  It will be easy to fix if you cannot.  You do not want to add a debian repository to your list.

Complain to the backport people...

---

### Post by DutchLau on 2005-05-19
Try this:

This is my sources list and it works fine for me.

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main 

I assume you're trying to install codecs so you can play media files, right? If so, follow these steps from the Ubuntu guide and you'll be okay  :) 

```
wget -c http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install liblame0
sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb
gst-register-0.8
``` 

Let us know once you've fixed it

DutchLau

---

### Post by Nick Post on 2005-05-19
Thanks everyone.  DutchLau, I'll add in that nerim stable main, and whatever I see that's missing from yours vs mine.  Also, I might # out some of the repositories that are getting me that O-named version.

I'll report back, if for no other reason so people can find the answer when searching.

Thanks again.

edited to add:  Yeah, doing the codec thing, working toward DVD::RIP.

---

### Post by Nick Post on 2005-05-19
Sucess.

Basically, adapting my resource list to be like DutchLau meant removing the backports and adding in the two other nerim ones.

Worked like a charm.

Hopefully, the next person with this prob will just find it with search.

---

### Post by wouter78 on 2005-06-01
Hi,

Installing gstreamer0.8-lame I got a dependency problem:

The following packages have unmet dependencies:
  gstreamer0.8-lame: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

What to do about that? My repositories are exactly the same as the last repository list in this thread.

Greetings, Wouter

---

### Post by mspohr on 2005-06-07
[QUOTE=DutchLau]Try this:

This is my sources list and it works fine for me.

 

I assume you're trying to install codecs so you can play media files, right? If so, follow these steps from the Ubuntu guide and you'll be okay  :) 

```
wget -c http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install liblame0
sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb
gst-register-0.8
``` 

Let us know once you've fixed it

DutchLau[/QUOTE]
 As a new user to Linux (and Ubuntu), I don't understand why it is so difficult to rip and play MP3s... 
I managed to get MP3 enabled by installing gstreamer0.8-mad but I'm stuck trying to get gstreamer0.8-lame installed.  I've enabled repositories in the list but I get a dependency problem.  I found liblame0 3.96.1-Osarge1 but gstreamer complains: gstreamer0.8-lame:
  Depends: liblame0 (>=3.96.1-1) but 3.96.1-0sarge1 is to be installed
Where can I find the proper liblame0?

BTW, I tried the wget ... frankandjacq.com... code but get a 404 not found so that must have moved.

---

