---
title: "why can't I apt-get !!!"
date: 2005-08-09
forum: General Help
---

### Post by cobelloy on 2005-08-09
AAAARRRRRGGGGGGHHHH!!!!!!

I finally had my crappy old P2 working nicely enough with ubuntu (but not enough power for dvd/video tasks) so I bought a secondhand P4/mobo/RAM and installed it in the case after pulling out the old stuff. First of all when I rebooted Xserver wouldn't work (maybe because it has onboard graphics - not the vid card I was using) and I had all manner of other problems too - so I thought, clean install on a spare HDD. Ubuntu installed OK but the live CDs of mepis and puppy did not work - they would hang at the beginning of the boot sequence.

Now I have a clean install of ubuntu with the previous HDD hooked up as slave and accessible from the desktop, but I would like to re-customise my new installation to how it was before and every time I try to apt-get update I get this:


...
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: Unknown error executing gpgv
W: GPG error: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hoary Release: Unknown error executing gpgv
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: Unknown error executing gpgv
W: GPG error: [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hoary-updates Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

and I have tried US repositories and GB repositories as well, I have tried copying the entire apt folder from the previous installation, I followed some instructions about importing a key, and I have pulled out some of my hair....none of it has made any difference.

please help

---

### Post by coolclassic on 2005-08-09
Try here it should help:
[https://wiki.ubuntu.com//AptAuthenticationInstructionsForHoary](https://wiki.ubuntu.com//AptAuthenticationInstructionsForHoary)

---

### Post by cobelloy on 2005-08-09
been there already...

that was the instructions about a key I was referring to, if the issue is still a key thing then I need keys for archive and security, marrillat is not a problem (although I think it was before I did the key thing)

anyone know where to get other keys?

---

### Post by coolclassic on 2005-08-10
can you show us your source list.

---

### Post by cobelloy on 2005-08-10
This is the sources.list that was in use before I upgraded the CPU/mobo and was working fine (and leads to the above mentioned error now) - I have tried many variations on the sources.list and all result in the same error

.........................................................................................................................

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

#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
#deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 


................................................................................................................

---

### Post by Suparious on 2005-10-24
I just had this problem last night/this morning...  :rolleyes: 

my system date/time were invalid....

---

