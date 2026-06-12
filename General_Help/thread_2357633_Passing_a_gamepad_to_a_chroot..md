---
title: "Passing a gamepad to a chroot."
date: 2017-04-04
forum: General Help
---

### Post by charononus on 2017-04-04
So I'm running Ubuntu xenial amd64  I needed to set up a chroot to get pcsx2 to work as it requires some packages that aren't compatible with what other programs need.  I got the chroot setup,  it works,  however it doesn't get input from my bluetooth gamepad.  Not sure what I need to set up to get it to do so.  

Here are my notes that I used for the setup.
```

Commands used to setup chroot
sudo apt install schroot
sudo apt install debootstrap
sudo mkdir /srv/chroot/xenial
sudo nano /etc/schroot/schroot.conf
Pasted this to the end of the file
[xenial]
description=Ubuntu Xenial 16.0.4 32-bit
directory=/srv/chroot/xenial
groups=sbuild-security
aliases=main
personality=linux32
sudo debootstrap --variant=buildd --foreign --arch i386 xenial /srv/chroot/xenial/ [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/)
sudo chroot /srv/chroot/xenial /debootstrap/debootstrap --second-stage
sudo schroot -c xenial -u root
nano /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
apt update
apt install ubuntu-standard
apt install ubuntu-desktop
apt install nvidia-375
add-apt-repository ppa:gregory-hainaut/pcsx2.official.ppa
apt update
apt install pcsx2
sudo mount -o bind /proc /srv/chroot/xenial/proc (system shell)
sudo cp /etc/resolv.conf /var/chroot/etc/resolv.conf (system shell)
export DISPLAY=:0.0
xhost + (system shell)
cd /usr/games
DISPLAY=:0.0 ./PCSX2
```
(system shell) is just a comment to myself that it was ran in a system terminal not a chrooted terminal. The install list could probably be reduced at somepoint, this is a huge install, but I went for brute force and didn't worry about disk space yet.

---

### Post by coffeecat on 2017-04-04
Support, not discussion. *Thread moved to **General Help**.*

---

### Post by charononus on 2017-04-04
Thank you.  New to these forums and just kind of guessed where to put it.

---

### Post by charononus on 2017-04-04
As an update I learned that the gamepad is /dev/input/js0 so I linked the /dev to the chroot in the system shell with:
```
sudo mount -o bind /dev /srv/chroot/xenial/dev
```
but I still got nothing inside the game.

---

