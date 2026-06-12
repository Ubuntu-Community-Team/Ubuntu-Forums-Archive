---
title: "errors trying to install handbrake-cli"
date: 2012-11-12
forum: General Help
---

### Post by sanderj on 2012-11-12
Ubuntu 12.10 64-bit, and I get the error message below trying to install handbrake-cli.

Isn't it strange it wants to install i386 libraries?

Anyway: tips appreciated



```
sander@R540:~$ sudo apt-get install handbrake-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 handbrake-cli:i386 : Depends: libdca0:i386 but it is not going to be installed
                      Depends: libdvdnav4:i386 (>= 4.2.0+20120524) but it is not going to be installed
                      Depends: libdvdread4:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
sander@R540:~$ 

```

---

### Post by sanderj on 2012-11-12
Solved! Here's how:

```
http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu

```

is now back in my /etc/apt/sources.list. I had put it there in a previous Ubuntu (12.04?), and it had been disabled by the Quantal upgrade:

> # disabled on upgrade to quantal

After enabling it, I'm able to install HandBrake

---

