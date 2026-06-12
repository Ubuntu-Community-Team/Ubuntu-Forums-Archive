---
title: "Repositories Help"
date: 2007-10-20
forum: General Help
---

### Post by Green_biri on 2007-10-20
First of all, sorry if this is the wrong section to post this Thread... Well, my problem is that when I try to update/install/etc. anything, I can't connect to the server were it's located what I want... If I try the **apt-get update** here's what it happens:

```
pedroguerra@Pedro:~$ sudo apt-get update
0% [Connecting to nl.archive.ubuntu.com (32.1.7.184)]

```

And It stays there...:(

By the way, this started happening when I upgraded to Gutsy Gibbon.

Any Help? Thanks.

---

### Post by chrisccoulson on 2007-10-20
I'm getting this too. I think it's just because the servers are overloaded with people upgrading to Gutsy. Try it later and see if it works

---

### Post by PmDematagoda on 2007-10-20
You could also try changing the server to a different location in Software Sources, it may solve your problem.

---

### Post by Green_biri on 2007-10-20
> **PmDematagoda said:**
> You could also try changing the server to a different location in Software Sources, it may solve your problem.

In **Sources.list**? What do I put there?

---

### Post by PmDematagoda on 2007-10-20
No, no, now you find Software Sources in System>Administration. When you enter it, you can change the server locations in the Ubuntu Software tab.

---

### Post by Green_biri on 2007-10-20
I changed it to a Portuguese server... Nearest location for me... But when I try updating it still says the same...:(:

```
pedroguerra@Pedro:~$ sudo apt-get update
0% [Connecting to nl.archive.ubuntu.com (32.1.7.184)] [Connecting to ubuntu.dcc.fc.up.pt (1.0.0.0)]

```

---

### Post by PmDematagoda on 2007-10-20
Then try another, such as the USA server, may be that will give you better luck.

---

### Post by Green_biri on 2007-10-21
> **PmDematagoda said:**
> Then try another, such as the USA server, may be that will give you better luck.

Well, I've even formatted my PC, installed a clean installation and still nothing!

C'mon, help?

---

### Post by chrisccoulson on 2007-10-21
Try the UK mirrors. They're working fine for me at the moment.

---

### Post by lukeminus on 2007-10-21
Hey I am getting this exact same problem, regardless of what server I change to. HELP :confused:

---

### Post by leeg on 2007-10-22
Hi, I've been have the same sort of problem but I am overcoming it at the moment by keep on clicking on the "Select best server" button in the software sources. This will allow me to connect just one time and maybe allow me to download  a program:), then next time I try to add a new program I have to do it again, usually selecting a different server to the one I connected to last time:(. I have also tried the medibuntu and debian repositries with no success at all.:(

---

### Post by Green_biri on 2007-10-22
Well, it's been the same for me... Anyone gets a solution? :(

---

### Post by lukeminus on 2007-10-23
I am still having this issue, has anyone got any solutions? Cheers

---

### Post by Green_biri on 2007-10-24
Cmon guys, it's really urgent... i can't download codecs, updates or any programs! Please...

---

### Post by PmDematagoda on 2007-10-26
Could you post your sources.list file using:-
```

gedit /etc/apt/sources.list
```

---

### Post by zaphod777 on 2007-10-26
how is your overal internet conectivity? no firewalls blocking ports etc?

---

### Post by GrumpyBob on 2007-10-26
This may well be the solution.  ISTR that when I was running Feisty, and my laptop was connected to my work network, I needed to change the repos from http:// to ftp:// 
(I used find and replace in gedit to make change - keep a backup copy of sources.list)

Robert

---

### Post by Green_biri on 2007-10-26
> **PmDematagoda said:**
> Could you post your sources.list file using:-
```

gedit /etc/apt/sources.list
```

Sure I could:

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://pt.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://pt.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://pt.archive.ubuntu.com/ubuntu gutsy
deb http://pt.archive.ubuntu.com/ubuntu gutsy-updates
deb http://security.ubuntu.com/ubuntu gutsy-security

deb http://packages.freecontrib.org/ubuntu/plf gutsy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf gutsy free non-free  
```

---

### Post by Green_biri on 2007-10-28
No answers?

---

### Post by lukeminus on 2007-10-28
> **GrumpyBob said:**
> This may well be the solution.  ISTR that when I was running Feisty, and my laptop was connected to my work network, I needed to change the repos from http:// to ftp:// 
(I used find and replace in gedit to make change - keep a backup copy of sources.list)

Robert

This method worked for me like a mint. I was having the exact same problem for a while, now there are no issues... as of yet anyway.

---

### Post by Green_biri on 2007-10-28
Well, I solved my problem... Downgraded it to Feisty again...:lolflag:

---

### Post by Green_biri on 2007-11-25
OK, I got to put this topic running again... after 4 weeks using Feisty Fawn I've decided to do a fresh install of Gutsy again... I've got the same problem: Got Internet, but can't install programs... _any_.

Here's my sources list:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
```

Please help me... this is driving me nuts!:(

---

### Post by PeterJS on 2007-11-25
I don't know if it's any consolation, but I can tell you that the problem isn't on your end, I just tried to ping that repository and there's nobody home.
Here's the complete list of repositories:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Try running through them until you find something that works. I'm using:
[http://ubuntu.osuosl.org/](http://ubuntu.osuosl.org/)
and can guarantee that it's up, but it's on the US west coast, so I'm not sure how much good it's going to do you.

---

### Post by Green_biri on 2007-11-26
So, I've chosen [this]("https://launchpad.net/ubuntu/+mirror/ftp.dei.uc.pt-archive") repository, which is the nearest to my home... how do I add it to the sources list? Just paste this code there?

```
http://ftp.dei.uc.pt/pub/linux/ubuntu/archive/
```

---

### Post by PeterJS on 2007-11-26
Yeah, pretty much. I'd suggest using a graphical text editor and using find and replace, instead of changing each entry by hand.

---

### Post by Green_biri on 2007-11-26
> **PeterJS said:**
> Yeah, pretty much. I'd suggest using a graphical text editor and using find and replace, instead of changing each entry by hand.

Ah... I just added it with **gedit /etc/apt/sources.list** but it gives me an error on the console when I do **apt-get update**:

```
E: The type 'http://ftp.dei.uc.pt/pub/linux/ubuntu/archive/' it's not known in the line 77 in the sources list /etc/apt/sources.list

```

(Translated from Portuguese)

What's the problem?

---

### Post by PeterJS on 2007-11-26
Could you paste line 77 in it's entirety?

I'm pretty sure that the problem is that you didn't specifiy a type either deb or deb-src. Also the fact that the line number is so high makes me think you didn't try replacing the exsisting entries which would be far easier than writing a new setup from scratch.

---

### Post by Green_biri on 2007-11-26
> **PeterJS said:**
> Could you paste line 77 in it's entirety?

I'm pretty sure that the problem is that you didn't specifiy a type either deb or deb-src. Also the fact that the line number is so high makes me think you didn't try replacing the exsisting entries which would be far easier than writing a new setup from scratch.

Here's my new sources list:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pt.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://pt.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

http://ftp.dei.uc.pt/pub/linux/ubuntu/archive/
```

---

### Post by PeterJS on 2007-11-26
Ah, ok see that last line before your new entry it says:
```

# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```
the # symbol at the front means to ignore it, so first we want to remove that from all the lines that deal with the main repositories, which is mostly that last block dealing with security and the archive.

On that note here's what the first two lines should look like after you have edited them
```

deb http://ftp.dei.uc.pt/pub/linux/ubuntu/archive/ gutsy main restricted
deb-src http://ftp.dei.uc.pt/pub/linux/ubuntu/archive/ gutsy main restricted

```
So the format of the entries is
<type> <server> <components>
What you want to do is change the sever bit and remove the # from each line.

---

### Post by rsambuca on 2007-11-26
Your repos are really messed up.  I suggest you just make a completely new list.  You can go to[ this site]("http://www.ubuntu-nl.org/source-o-matic/") to generate a new one.

---

### Post by erfahren on 2007-11-26
to add that new repository see this: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

the other problem now is tha all of the other ones are commented out. Gutsy does that when you install and not connected to the internet (seems to be a new thing, it's confusing others as well).

You can either try enabling them again through Synaptic Software Sources or uncomment all the deb and deb-src lines.

one other thing is you could change it all (back it up first), see: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)
if you do that remember to add the key for Mediubuntu (instructions in the guide).

---

### Post by Green_biri on 2007-11-26
> **rsambuca said:**
> Your repos are really messed up.  I suggest you just make a completely new list.  You can go to[ this site]("http://www.ubuntu-nl.org/source-o-matic/") to generate a new one.

Ok, I followed your advice and my new sources list is:

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://pt.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://pt.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://pt.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://pt.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse
```

But then I apt-get update and it just stays:

```
Err http://security.ubuntu.com gutsy-security Release.gpg                               
  It was not possible to connect to security.ubuntu.com:80 (1.0.0.0), the connection expired
Err http://pt.archive.ubuntu.com gutsy Release.gpg                                      
  It was not possible to connect to pt.archive.ubuntu.com:80 (1.0.0.0), the connection expired
0% [Connecting to pt.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
```

---

### Post by rsambuca on 2007-11-26
Pick another location.

---

### Post by Green_biri on 2007-11-26
> **rsambuca said:**
> Pick another location.

Still the same...:(

---

### Post by erfahren on 2007-11-26
do you connect through a proxy or have a direct internet connection?

I'm trying this search right now (I took out the "pt" part to hopefully get more results)
[http://www.google.com/search?hl=en&q=0%25+%5BConnecting+to+archive.ubuntu.com+%281.0.0.0%29%5D&btnG=Google+Search](http://www.google.com/search?hl=en&q=0%25+%5BConnecting+to+archive.ubuntu.com+%281.0.0.0%29%5D&btnG=Google+Search)

---

### Post by retrow on 2007-11-26
Install [automatix2]("http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.10_.28Gutsy_i386.29"). It will add its own repository paths to sources.list and update the list. Regardless of Ubuntu sources, automatix2 should be able to access its own repositories. If automatix2 fails, you definitely have some network problem.

---

### Post by smartboyathome on 2007-11-26
Use the Software Sources tool in System > Administration, and click other on the dropdown box, and click best server, if none of them work, it should tell you. If that is the case you are behind a proxy (most likely).

---

### Post by erfahren on 2007-11-26
ok check this out: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/156720](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/156720)

got to there from here: [https://bugs.launchpad.net/ubuntu/+bug/81057](https://bugs.launchpad.net/ubuntu/+bug/81057)

It sounds like there was a bug that an update fixed, BUT because of the bug you can't get the update. 

So you just got to download and install it manually. 

This is a little above my personal expertise at this time, but it seems from what I read that the bug was fixed but not contained in the original releases of Gutsy. I may be wrong about this but if that was the case you may have gotten a earlier version.

It's obvious that the problem is a general network problem, and not just with the repositories you're trying to connect to. You haven't been able to connect to any (Automatix is definitely not the answer!).

I found the package that glibc is contained in, but I don't know if you can just install the whole thing or not. Hopefully someone will "chime in" on this who has more experience with this.
EDIT: here's the link - [http://packages.ubuntu.com/gutsy/virtual/glibc-2.6-1](http://packages.ubuntu.com/gutsy/virtual/glibc-2.6-1)

---

### Post by Green_biri on 2007-11-26
> **retrow said:**
> Install [automatix2]("http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.10_.28Gutsy_i386.29"). It will add its own repository paths to sources.list and update the list. Regardless of Ubuntu sources, automatix2 should be able to access its own repositories. If automatix2 fails, you definitely have some network problem.

I tried to install automatix2 but it gave me an error:

```
Error: Dependency is not satisfiable: tango-icon-theme-common
```

> **smartboyathome said:**
> Use the Software Sources tool in System > Administration, and click other on the dropdown box, and click best server, if none of them work, it should tell you. If that is the case you are behind a proxy (most likely).

Ok, I did that and when I tried **apt-get update** it read all the packages... but when I tried to update the programmes using the manager, it just didn't download anything... so I cancelled it, got back to the console and did **apt-get update** again... but now it still says that it's connecting...:confused:

---

### Post by Green_biri on 2007-11-26
Ok guys, lemme update my situation:

So I went again to Software Sources tool in System > Administration and chose "Best Server" in others... then I opened Update Manager as fast as I could and clicked "Install Actualizations"... And, I really don't know how but it downloaded all of the actualizations! Now I'm waiting for it to install... Let's hope that the **libc6** package solve my problem!

Edit: It worked! :D I really dunno how but thank you for all the support guys... ;)

---

### Post by erfahren on 2007-11-26
> **Green_biri said:**
> 
Edit: It worked! :D I really dunno how but thank you for all the support guys... ;)
=D>

---

### Post by retrow on 2007-11-26
Fantastic!

Now first order of business should be installing automatix2, the one I suggested earlier in this thread. Through automatix2 you can get most of the popular codecs and plugins that you would normally require for opening and running applications.

---

### Post by rsambuca on 2007-11-26
> **retrow said:**
> Fantastic!

Now first order of business should be installing automatix2, the one I suggested earlier in this thread. Through automatix2 you can get most of the popular codecs and plugins that you would normally require for opening and running applications.

Automatix really is not necessary, and can do some rather undesireable things to your system.

---

### Post by retrow on 2007-11-26
It makes life much easier though. If there were any undesirable changed BECAUSE of the way automatix installed some packages, they were beyond my ability to compreend, i.e. it made no difference at the level I work at. I agree you can do most of that stuff through Synaptic or getting .deb files directly from the appropriate websites, but perhaps I'm too lazy and just like to sit back and let the scripts run by themselves :popcorn:

---

### Post by rsambuca on 2007-11-26
Everything is pretty automated in Gutsy nowadays.  You get prompted to install flash and/or java the first time you visit a site that requires it.  Same with codecs.  Restricted Drivers manager for video drivers.

---

### Post by erfahren on 2007-11-26
> **retrow said:**
>  ...I agree you can do most of that stuff through Synaptic ...
I don't think there's anything available through automatix that's not available in the Gutsy repositories. 

It's been said before, automatix may have had its place before but it really isn't needed anymore. I can make a list of all the things I want that automatix would install, search Synaptic for them and painlessly install them. May take a few moments longer, but without the potential (major) problems.

here's a list of the first things I installed through Synaptic after installing Gutsy (just going through Synaptic and checking off stuff that I thought of). How can that be beat?
Installed the following packages:
bubblemon (2.0.5-2)
cabextract (1.2-2)
computertemp (0.9.6.1-1)
gdesklets (0.35.3-4ubuntu2)
gdesklets-data (0.35.6-1ubuntu1)
gsynaptics (0.9.12-0ubuntu1)
java-common (0.26ubuntu1)
libaudio2 (1.9-2)
libqt3-mt (3:3.3.8really3.3.7-0ubuntu11)
msttcorefonts (2.2)
nautilus-open-terminal (0.8-1ubuntu1)
odbcinst1debian1 (2.2.11-16)
opera (9.24-20071015.6gutsy1)
sun-java6-bin (6-03-0ubuntu2)
sun-java6-jre (6-03-0ubuntu2)
sun-java6-plugin (6-03-0ubuntu2)
thunderbird (2.0.0.6+nobinonly-0ubuntu1)
ttf-ubuntu-title (0.1-1)
unixodbc (2.2.11-16)

---

