---
title: "installing apps such as vlc"
date: 2005-07-06
forum: General Help
---

### Post by Vega on 2005-07-06
well I finally got on the bandwagon and I'm impressed. The deal is I'm migrating from windows and I'm  trying to install apps such as vlc; I'm use to of course setting up exe files and I find it kind of complicated on debian since I know nothing about it.


In this pic where do I start from here?

---

### Post by angkor on 2005-07-06
Welcome to Ubuntu :)

First of all read the [Ubuntu Starter Guide](http://www.ubuntuguide.org)...it'll be of great help.

Second you can use a program called Synaptic to install software. (like vlc)

System->Administration->Synaptic Package Manager

You will be prompted for your user passwd.

Good luck.

---

### Post by Vega on 2005-07-06
[QUOTE=angkor]Welcome to Ubuntu :)

First of all read the [Ubuntu Starter Guide](http://www.ubuntuguide.org)...it'll be of great help.

Second you can use a program called Synaptic to install software. (like vlc)

System->Administration->Synaptic Package Manager

You will be prompted for your user passwd.

Good luck.[/QUOTE]

man I'm so lost  ](*,)

---

### Post by angkor on 2005-07-07
Is there any particular reason you insist on compiling vlc? What I meant to say is that vlc is available from the repositories and simply installable through synaptic. I don't know much about synaptic but I do know 'sudo apt-get install vlc' will work.

---

### Post by cobelloy on 2005-07-07
hi there,

I love VLC, so I can tell you hoe to get it, on the webpage that you took a snapshot of there are two lines that start with hash symbols, copy those (highlight then copy)

I find it easier to work as root, so if you dont have a root account yet find the entry on the starter guide to creating a root account.

then open a console, type su [enter] then your root password [enter] then type gedit /etc/apt/sources.list

an editor application will start, firstly go to file - save as and save as sourceslist.bak (incase you need this list again)

this file has a whole bunch of entries starting with hashes, delete the hashes that are before ftp and http site URLs if they still have hashes, then insert the two lines you copied from VLC website, save as sources.list (don't just click save - or you will just overwrite the backup you made.

close the editor and go back to your console, type in apt-get update [enter] and when that is done type in apt-get install vlc

that should take care of it.

if you cant figure out how to open vlc, just open a console and type vlc [enter]

hope this helps, I only just switched myself and getting started is really hard, but it is like a snowball once you get going a bit :)

---

### Post by cobelloy on 2005-07-07
sorry - the two lines you copy start with "deb" the hash symbol lines are console commands

sorry - still a bit new

---

### Post by cobelloy on 2005-07-07
try reading these sections of the starter guide first:

How to add extra repositories

and

How to set/change/enable root user password

they might help you understand what I wrote up there ^ I am not a good explainer

---

### Post by Vega on 2005-07-07
[QUOTE=cobelloy]hi there,

I love VLC, so I can tell you hoe to get it, on the webpage that you took a snapshot of there are two lines that start with hash symbols, copy those (highlight then copy)

I find it easier to work as root, so if you dont have a root account yet find the entry on the starter guide to creating a root account.

then open a console, type su [enter] then your root password [enter] then type gedit /etc/apt/sources.list

an editor application will start, firstly go to file - save as and save as sourceslist.bak (incase you need this list again)

this file has a whole bunch of entries starting with hashes, delete the hashes that are before ftp and http site URLs if they still have hashes, then insert the two lines you copied from VLC website, save as sources.list (don't just click save - or you will just overwrite the backup you made.

close the editor and go back to your console, type in apt-get update [enter] and when that is done type in apt-get install vlc

that should take care of it.

if you cant figure out how to open vlc, just open a console and type vlc [enter]

hope this helps, I only just switched myself and getting started is really hard, but it is like a snowball once you get going a bit :)[/QUOTE]


I just got this one error that it can't find the vlc package, I'm seem to be going in the right path, can you tell me what I need to do?

after a few minutes I accidentaly saved the main sources.list with 2 urls and can't erase em

---

### Post by cobelloy on 2005-07-07
this is my sources.list:

--------------------------------------------------------------------

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
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

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

-----------------------------------------------------------

everything between the lines is the sources.list, if you want a copy of my backup list you can have it too.

replace your entire list with this one, then try apt-get update, then apt-get install vlc.

something else I noticed on the forums, 

if you get the md5sum error try #ing out the us.archive.ubuntu entries, I don't know if it works but someone suggested it in another thread, also sometimes the repositories are down or faulty, how long have you been trying to do this for?

well, good luck...again

---

### Post by Vega on 2005-07-07
[QUOTE=cobelloy]this is my sources.list:

--------------------------------------------------------------------

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
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

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

-----------------------------------------------------------

everything between the lines is the sources.list, if you want a copy of my backup list you can have it too.

replace your entire list with this one, then try apt-get update, then apt-get install vlc.

something else I noticed on the forums, 

if you get the md5sum error try #ing out the us.archive.ubuntu entries, I don't know if it works but someone suggested it in another thread, also sometimes the repositories are down or faulty, how long have you been trying to do this for?

well, good luck...again[/QUOTE]


3 and 1/2 hrs. the deal is it says I can't replace it. I don't have permission.

I thank you for your efforts

---

### Post by drummer on 2005-07-07
sources.list must be opened by root to edit it (your last screenshot had it open with [read-only] in the title bar). so do this```
sudo gedit /etc/apt/sources.list
``` and you will be able to edit the file. remember whenever changes have been made to do a```
sudo apt-get update
```to update the sources. You need the lines from the vlc site if you want the latest version (0.8.2) otherwise version 0.8.1 is in the 'Universe' Ubuntu repository.

Then go ahead and do```
sudo apt-get install vlc
```this should install the latest version of vlc available.

Also go to [www.ubuntuguide.org](www.ubuntuguide.org) and install the extra multimedia codecs if you haven't already.

---

### Post by Vega on 2005-07-07
[QUOTE=drummer]sources.list must be opened by root to edit it (your last screenshot had it open with [read-only] in the title bar). so do this```
sudo gedit /etc/apt/sources.list
``` and you will be able to edit the file. remember whenever changes have been made to do a```
sudo apt-get update
```to update the sources. You need the lines from the vlc site if you want the latest version (0.8.2) otherwise version 0.8.1 is in the 'Universe' Ubuntu repository.

Then go ahead and do```
sudo apt-get install vlc
```this should install the latest version of vlc available.

Also go to [www.ubuntuguide.org](www.ubuntuguide.org) and install the extra multimedia codecs if you haven't already.[/QUOTE]

many many thanks man! I tried to install vlc now but the pic says this

---

### Post by GMachine_24 on 2005-07-07
Dude - you need to be logged in as root. Click applications>system tools>root terminal and try again.

Best of luck.

---

### Post by Vega on 2005-07-07
[QUOTE=GMachine_24]Dude - you need to be logged in as root. Click applications>system tools>root terminal and try again.

Best of luck.[/QUOTE]

but I am. the pic says the package isn't found and I don't know how to make it find it.

---

### Post by GMachine_24 on 2005-07-07
Yeah - to be honest I'm having the same problem - and then some. My back aches and so does my a** so I think I'm going to call it a night. But.... I urge you not to give up. I have used Videolan on a RedHat 9.0 machine and it worked great. There is always an answer to every problem; we just need to find it.

In memory of those lost today in London and Iraq - may everyone have a good night.

GMachine

---

### Post by cobelloy on 2005-07-07
well, I don't know any thin else, I still get this on my machine:

cobelloy@blackBOX:~$ su
Password:
root@blackBOX:/home/cobelloy # apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdvbpsi3 libid3tag0 libmpeg2-4 libtar libwxgtk2.5.3 wxvlc
Suggested packages:
  vlc-plugin-alsa mozilla-plugin-vlc
Recommended packages:
  ttf-thryomanes videolan-doc
The following NEW packages will be installed:
  libdvbpsi3 libid3tag0 libmpeg2-4 libtar libwxgtk2.5.3 vlc wxvlc
0 upgraded, 7 newly installed, 0 to remove and 49 not upgraded.
Need to get 311kB/8718kB of archives.
After unpacking 23.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe wxvlc 0.8.1-1ubuntu7 [311kB]
Fetched 311kB in 30s (10.2kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.1-1ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.1-1ubuntu7_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@blackBOX:/home/cobelloy # exit
exit
cobelloy@blackBOX:~$


I haven't tried editing my list yet, will post again

---

### Post by cobelloy on 2005-07-07
this is very interesting - I just edited sources.list to comment out all but the VLC repositories and I get this now:

root@blackBOX:/home/cobelloy # apt-get update
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release.gpg
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Packages
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Sources
Hit [http://download.videolan.org](http://download.videolan.org) sarge/main Packages
Hit [http://download.videolan.org](http://download.videolan.org) sarge/main Sources
Reading package lists... Done
root@blackBOX:/home/cobelloy # apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc
root@blackBOX:/home/cobelloy #


anyone else know why you can't get vlc from the vlc repositories?

---

### Post by Vega on 2005-07-07
[QUOTE=cobelloy]this is very interesting - I just edited sources.list to comment out all but the VLC repositories and I get this now:

root@blackBOX:/home/cobelloy # apt-get update
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release.gpg
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Packages
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Sources
Hit [http://download.videolan.org](http://download.videolan.org) sarge/main Packages
Hit [http://download.videolan.org](http://download.videolan.org) sarge/main Sources
Reading package lists... Done
root@blackBOX:/home/cobelloy # apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc
root@blackBOX:/home/cobelloy #


anyone else know why you can't get vlc from the vlc repositories?[/QUOTE]

Haha! oh man what are we gonna do!?

---

### Post by drummer on 2005-07-07
I'm not sure why this isn't working, maybe there is a problem with the packages on the vlc repos. Try removing the vlc repos from the list and just uncommenting the 4 universe lines (then 'sudo apt-get update' before installing).. the version is only one behind the latest and I've had no problems with the version from Universe.

---

### Post by cobelloy on 2005-07-07
I commented out universe and vlc repositories, others back in, and get this:

root@blackBOX:/home/cobelloy # apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release [26.2kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages [490kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources [175kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources [1320B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages [6335B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages [14B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources [1963B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources [14B]
Fetched 722kB in 1m22s (8794B/s)
Reading package lists... Done
root@blackBOX:/home/cobelloy # apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc


there must be some problem with vlc at the moment,maybe it is off the repositories for now.

---

### Post by Vega on 2005-07-08
[QUOTE=cobelloy]I commented out universe and vlc repositories, others back in, and get this:

root@blackBOX:/home/cobelloy # apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release [26.2kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages [490kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources [175kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources [1320B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages [6335B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages [14B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources [1963B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources [14B]
Fetched 722kB in 1m22s (8794B/s)
Reading package lists... Done
root@blackBOX:/home/cobelloy # apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc


there must be some problem with vlc at the moment,maybe it is off the repositories for now.[/QUOTE]

I actually tried yum and it does the same thing.

---

### Post by kepsux on 2005-07-08
Heh, I'm trying to install vlc as well and getting the same error. Anyone come up with a fix? I tried using sid instead of sarge and got some dependency errors instead seen here:

```
root@katherine:/home/eric # apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libdvbpsi2 but it is not installable
       Depends: libdvdplay0 but it is not installable
       Depends: libflac4 but it is not installable

```

I was going to try and compile from source, but the dependency list is a nightmare.

---

### Post by GMachine_24 on 2005-07-08
Just checking back in. At least now I don't feel like it's "just me". Someone should file a bug report - I would, but I've never done it. Any volunteers?

---

### Post by Vega on 2005-07-08
[QUOTE=GMachine_24]Just checking back in. At least now I don't feel like it's "just me". Someone should file a bug report - I would, but I've never done it. Any volunteers?[/QUOTE]

oh man! This is serious.

---

### Post by sfabel on 2005-07-09
Hi,

this is my /etc/apt/sources.list:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

And I just installed vlc in Version "0.8.1-1ubuntu7" which seems to be the latest as of now.

"apt-get install vlc".

HTH,
Stephan

---

### Post by cobelloy on 2005-07-09
I have followed some advice in another thread, and changed the US repositories to GB ones, and now apt-get is working fine, here is a copy of my sources list now:

-----------------------------------------------

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

# deb [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sarge main 
# deb-src [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sarge main 

-----------------------------------------------------

I have commented out the VLC repositories since they weren't giving me anything. But I just installed a whole bunch of things including VLC that were not previously installable (which is weird - because before I read your first post my apt-get was working fine)

anyway, hopefully this will put an end to the crazyness once and for all....

---

### Post by Vega on 2005-07-09
[QUOTE=cobelloy]I have followed some advice in another thread, and changed the US repositories to GB ones, and now apt-get is working fine, here is a copy of my sources list now:

-----------------------------------------------

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

# deb [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sarge main 
# deb-src [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sarge main 

-----------------------------------------------------

I have commented out the VLC repositories since they weren't giving me anything. But I just installed a whole bunch of things including VLC that were not previously installable (which is weird - because before I read your first post my apt-get was working fine)

anyway, hopefully this will put an end to the crazyness once and for all....[/QUOTE]

thank goodness. ok so I should replace my sources.list with yours. Does this mean I replace the main sources.list by copy and pasting yours?

---

### Post by Vega on 2005-07-09
[QUOTE=cobelloy]I have followed some advice in another thread, and changed the US repositories to GB ones, and now apt-get is working fine, here is a copy of my sources list now:

-----------------------------------------------

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

# deb [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sarge main 
# deb-src [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sarge main 

-----------------------------------------------------

I have commented out the VLC repositories since they weren't giving me anything. But I just installed a whole bunch of things including VLC that were not previously installable (which is weird - because before I read your first post my apt-get was working fine)

anyway, hopefully this will put an end to the crazyness once and for all....[/QUOTE]


finally got it working but it dosn't even play divx files... Thanks everyone for all your help.

---

### Post by drummer on 2005-07-09
```
sudo apt-get install w32codecs
```That should get divx working, as well as any other originally-Windows codec.

---

### Post by cobelloy on 2005-07-09
there are a whole bunch of codecs listed in the starter guide to apt-get install. my VLC plays everything, including divX avi and I have all the codecs installed

---

