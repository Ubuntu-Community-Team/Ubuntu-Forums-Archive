---
title: "Unmet Dependencies Installing Plone"
date: 2006-12-05
forum: General Help
---

### Post by ewan11 on 2006-12-05
Hi,

I'm a noob with Ubuntu, and i tried to install Plone on my machine.
I used sudo apt-get install Plone but met with some dependency problems...
..I then did the sudo apt-get -f install as suggested to correct these broken dependencies.... but i get this error instead...

> 
zaki@zaki-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  libstdc++6: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies> 

Could someone kindly explain what this error message means and how i can go about fixing it or overcoming it?....

I also tried to fix there broken packages on Synaptic... but i get this error message which is the same error messages i had gotten initially:


> 
Synaptic Manager error
Could not apply changes!
Fix broken packages first> 



Can someone please enlighten me and give me a helping hand please.. thanks alot!

---

### Post by RAOF on 2006-12-05
You've got some Debian repositories in your sources.list, haven't you.

Please post the contents of the /etc/apt/sources.list file, and we'll be able to clean it up for you.

---

### Post by ewan11 on 2006-12-05
Hi RAOF, thanks so much for the help.... I have no idea why you need to see this list.. but here it is...what do i do now?... thanks again! cheers!




# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by adamkane on 2006-12-05
What method are you using to install Plone? Did you download it from the NET?

---

### Post by RAOF on 2006-12-05
I stand corrected.  That sources.list seems correct.  A broken sources.list is what most often causes the problem you describe.  Since that seems ok, I'm a bit at a loss.

Maybe someone else with more current Dapper knowledge (it's been a while since I've done anything on a Dapper system) can help you.

---

