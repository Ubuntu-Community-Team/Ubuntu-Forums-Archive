---
title: "Installing bumblebee on 12.04.2"
date: 2013-03-26
forum: General Help
---

### Post by katanacb on 2013-03-26
Hi there,

I'm trying to install bumblebee on ubuntu 12.04.2, 64-bit.  I have a Dell Precision M6600 with an nvidia optimus card.

I've followed the directions on [https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)   but I'm running into unsolved dependency errors.   Specifically, I'm getting this:

$ sudo apt-get install bumblebee bumblebee-nvidia
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 bumblebee-nvidia : Depends: nvidia-current but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11
                  Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.


seems like some sort of unsolvable dependency problem.   Also, I don't want to use nvidia-current, I want to use the 3.10 driver which supposedly is possible.   Does anyone know what I'm missing or what silly mistake I'm making here?

---

### Post by katanacb on 2013-04-03
*bump*

---

### Post by katanacb on 2013-04-16
OK, I guess I'll keep hacking away at this on my own and post if I figure it out.

---

