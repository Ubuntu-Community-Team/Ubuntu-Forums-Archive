---
title: "Synaptic does not connect to any repository"
date: 2015-10-04
forum: General Help
---

### Post by wilfried3 on 2015-10-04
I installed synaptic on a fresh Ubuntu 14.04.3, updated all (that worked fine, so it uses a repository in that stage since about 600MB where downloaded to do the update)

After the update and reboot I wanted to install additional software... And since I prefer Synaptic I took that..
sudo apt-get install synaptic   that worked fine.

Then I started synaptic, but to mu surprise it did not have a connection to a repository
when i search for applications nothing is found. 

I tried switching back to main server or let it find the fastest server. But Main server, fastest server and even other manually picked servers don't seem to connect to a repository.

How do I fix this?
=========================================
EDIT
The issue is a bit weirder...
Turns out that the repository works, but that the quick search is acting up

Whatever search I put in it gives an empty result.
for instance:
sysinfo
hardinfo
ssh

it doesn't find any of them

---

### Post by oldos2er on 2015-10-04
You might need to install *apt-xapian-index* ```
sudo apt-get install apt-xapian-index
``` Let me know if this works or not.

---

### Post by wilfried3 on 2015-10-04
Thanks, but it didn't work. 'newest version of xapian-index is already installed' message, 

I have looked at the filters and they seem to be ok, it's almost like a filter setting is inverted.  When i do a quick search for lets say gedit, then it finds the installed gedit package

So it does semi work, installed packages are displayed and non-installed packaged are not. they stay hidden (?)

---

### Post by oldos2er on 2015-10-04
Darn, I thought that would work. Hopefully someone more knowledgeable can help you.

---

### Post by mc4man on 2015-10-05
Does an actual search work? (Search icon
Maybe take a screenshot of the synaptic window in a failed "Quick filter" search,  alt+PrtSc

---

### Post by wilfried3 on 2015-10-07
Yes, I actually CAN search.

But that results only in a list of installed packages that match the search

So if i search for Office then it finds the installed office packages, but NOT the ones that I want to add.
If i delete the search word then i DO see ALL non installed packages, and i can manually scroll aaaaaaaaaaaaaaaaaaaaaaaaaaall the way down though thousands of packages and find the one i was looking for, and even can install it!

However it's a headache to do so..

If i search for lets say 'sysinfo' then the result is nothing.  However I'm able to install it manually as described above. or from the command line...  But i need to install many packages and don't know them all by name.

Its one of the weirdest situations i had with ubuntu. :-)
I have tried to reinstall synaptic but the issue is still there

---

### Post by ian-weisser on 2015-10-07
> **wilfried3 said:**
> But that results only in a list of installed packages that match the search

Sounds like perhaps your local dpkg database has not populated from your sources.

Check that your sources in /etc/apt/sources.list are valid
Run '*sudo apt-get update*' to update the database from your sources. Please show us the output.

---

### Post by wilfried3 on 2015-10-07
As i wrote above i also tried to switch servers, and after switching servers press the reload button. 
Actually i always reload, it's the first thing i do when synaptic is started. I'm not behind that PC at this moment, I'll show sources.list in my next post.

---

### Post by wilfried3 on 2015-10-07
sources.list

> 
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty main restricted
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates main restricted
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty universe
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-backports main restricted universe multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-backports main restricted universe multiverse

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-security main restricted
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-security main restricted
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-security universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-security universe
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-security multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main


Actually after every change to the sources.list synaptic presents a popup with a "reload" button

---

### Post by wilfried3 on 2015-10-08
How can i see what other packages are related to the quick search?

---

### Post by ian-weisser on 2015-10-08
The output of 'sudo apt-get update' may shed more light.

---

### Post by wilfried3 on 2015-10-08
sudo apt-get update

```

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release
Ign [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty InRelease                         
Get:1 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates InRelease [64.4 kB]     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources           
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports InRelease               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security InRelease            
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                     
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty Release                       
Get:2 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/main Sources [237 kB]
Get:3 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/restricted Sources [4,722 B]
Get:4 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/universe Sources [140 kB]
Get:5 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/multiverse Sources [5,144 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:6 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/main amd64 Packages [628 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                   
Get:7 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/restricted amd64 Packages [15.4 kB]
Get:8 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/universe amd64 Packages [321 kB]
Get:9 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:10 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/main i386 Packages [608 kB]
Get:11 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/restricted i386 Packages [15.1 kB]
Get:12 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/universe i386 Packages [322 kB]
Get:13 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/multiverse i386 Packages [12.1 kB]
Get:14 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/main Translation-en [305 kB]
Get:15 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/multiverse Translation-en [6,148 B]
Get:16 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/restricted Translation-en [3,569 B]
Get:17 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-updates/universe Translation-en [169 kB]
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/main Sources
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/restricted Sources
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/universe Sources
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/multiverse Sources
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/main amd64 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/restricted amd64 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/universe amd64 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/multiverse amd64 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/main i386 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/restricted i386 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/universe i386 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/multiverse i386 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/main Translation-en
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/multiverse Translation-en
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/restricted Translation-en
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-backports/universe Translation-en
Get:18 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/main Sources [96.9 kB]
Get:19 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/restricted Sources [3,357 B]
Get:20 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/universe Sources [31.0 kB]
Get:21 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/multiverse Sources [2,341 B]
Get:22 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/main amd64 Packages [350 kB]
Get:23 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/restricted amd64 Packages [12.4 kB]
Get:24 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/universe amd64 Packages [117 kB]
Get:25 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/multiverse amd64 Packages [3,691 B]
Get:26 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/main i386 Packages [333 kB]
Get:27 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/restricted i386 Packages [12.2 kB]
Get:28 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/universe i386 Packages [117 kB]
Get:29 [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/multiverse i386 Packages [3,833 B]
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/main Translation-en
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/multiverse Translation-en
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/restricted Translation-en
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty-security/universe Translation-en
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/main Sources
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/restricted Sources
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/universe Sources
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/multiverse Sources
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/main amd64 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/restricted amd64 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/universe amd64 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/multiverse amd64 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/main i386 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/restricted i386 Packages
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/universe i386 Packages         
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/multiverse i386 Packages       
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/main Translation-en            
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/multiverse Translation-en    
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/restricted Translation-en
Hit [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/universe Translation-en 
Ign [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/main Translation-en_US        
Ign [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/multiverse Translation-en_US 
Ign [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/restricted Translation-en_US 
Ign [http://mirror.i3d.net/pub/ubuntu/](http://mirror.i3d.net/pub/ubuntu/) trusty/universe Translation-en_US   
Fetched 3,950 kB in 9s (398 kB/s)                                              
Reading package lists... Done

```

---

### Post by ian-weisser on 2015-10-08
What is the result of 'apt-cache show sysinfo' ?
Is it blank/null, or is the database entry shown?

If blank/null, then there's a problem with apt...or the source.
If apt-cache works, then the problem seems with Synaptic.

---

### Post by wilfried3 on 2015-10-08
apt-cache show sysinfo

> 
Package: sysinfo
Priority: optional
Section: universe/utils
Installed-Size: 358
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian CLI Applications Team <pkg-cli-apps-team@lists.alioth.debian.org>
...
etc.



It looks like the filter config is somehow 'damaged'. Tough when I compare the filter settings checkboxes with an other system they are all identical.
Only the *default installed* pagages seem to be searched in.

I manually installed hardinfo and sysinfo (and a few other packages)
But when i search for those they also don't show.  
However when i search for office, then it shows the installed office packages, but NOT the additional ones i installed manually. :-) 
So it has very selective behaviour....
Not sure if that helps to find the cause of this...

---

### Post by mc4man on 2015-10-09
Maybe open synaptic, do a failed search  (sysinfo will do
Then take a window screenshot & post (alt+print key

---

### Post by wilfried3 on 2015-10-09
[[img]http://s2.postimg.org/umbuw3dk5/Screenshot_from_2015_10_09_11_53_31.png[/img]](http://postimg.org/image/umbuw3dk5/)
Synaptic loads all looks normal


[[img]http://s2.postimg.org/3zze749d1/Screenshot_from_2015_10_09_11_54_23.png[/img]](http://postimg.org/image/3zze749d1/)
I search for hardinfo, no results.


[[img]http://s2.postimg.org/43t7ndeud/Screenshot_from_2015_10_09_11_55_06.png[/img]](http://postimg.org/image/43t7ndeud/)
I searc for sys (first 3 letters of sysinfo) i see many INSTALLED packages that contain the word sys, but sysyinfo is not listed
 

[[img]http://s2.postimg.org/pc6w4stb9/Screenshot_from_2015_10_09_11_55_50.png[/img]](http://postimg.org/image/pc6w4stb9/)
when i complete the word sysinfo i get no results at all


[[img]http://s2.postimg.org/zc1skp4kl/Screenshot_from_2015_10_09_11_56_25.png[/img]](http://postimg.org/image/zc1skp4kl/)
also when i switch views from status to sections (or any other view) no results... Same when i search for other packages


[[img]http://s2.postimg.org/ljndp2dt1/Screenshot_from_2015_10_09_11_57_09.png[/img]](http://postimg.org/image/ljndp2dt1/)
sections view for 'sys'


[[img]http://s2.postimg.org/j3lkb7vqd/Screenshot_from_2015_10_09_12_05_38.png[/img]](http://postimg.org/image/j3lkb7vqd/)
when NO search word is entered and i scroll aaaaaaall the way down sysinfo is being listed just fine...

WTF? :-)

---

### Post by wilfried3 on 2015-10-11
Does this quick search have somekind of config file?

---

