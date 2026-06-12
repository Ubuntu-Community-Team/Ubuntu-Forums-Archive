---
title: "Gnome crashes cannot read source cache"
date: 2007-04-05
forum: General Help
---

### Post by YODAR on 2007-04-05
I get this from update icon

"AN error occurred.Please run package manager from the right click menue or Apt-get on a terminal to see what is wrong. The error message was: Error:opening cache (E:type 'wget' is not known on line 37 in source list /etc/apt/sources list E:the list of sources could not be read)

===============================


  SOURCE LIST
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
##N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
##team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
##extensively as that contained in the main release, although it includes
##newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
 [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2
echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo tee -a /etc/apt/sources.list

deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

