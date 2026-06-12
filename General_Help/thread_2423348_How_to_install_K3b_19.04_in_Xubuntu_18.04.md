---
title: "How to install K3b 19.04 in Xubuntu 18.04"
date: 2019-07-21
forum: General Help
---

### Post by Ralph L on 2019-07-21
Because the Xubuntu version of K3b (Version 17.12.3)  is lacking a few things I would like, I tried to install the latest version (19.0.4) from source into Xubuntu 18.04.  I came up with a bunch of missing dependencies, which were basically KF5 Version 5.48.0.  When I looked into that, I found that there were about 70 packages that needed installed, and I think they had to do with the Plasma system.  My first question is:  If I install the KF5 Version 5.48 packages, would I mess up Xubuntu, since it doesn't use Plasma??????  My next question is:  How do I do it (depending on whether it is a smart thing to do on Xubuntu)??????

Any help appreciated.....

---

### Post by CatKiller on 2019-07-21
Installing KF5 stuff in Xubuntu isn't *that* bad. Obviously it's a whole bunch of stuff that's duplicating what's provided by Xfce, which will have a larger footprint on disc and in RAM than something native, and larger than it would be if you were already running Plasma for everything else.

Installing a whole bunch of KF5 stuff from outside the repositories, because it's much newer than the versions in the repositories, is dependency hell just waiting to happen.

Installing a whole bunch of KF5 stuff from outside the repositories *from source* is going to be a complete pain. I certainly wouldn't do it.

What you want to do *is* (probably) possible, but I definitely wouldn't recommend it, and I don't see anything in the changelog for K3b that would warrant that much effort.

---

### Post by SeijiSensei on 2019-07-22
You could try building from source, but first you will need to uncomment any deb-src lines in /etc/apt/sources.list, then run "sudo apt update".

Next you can take advantage of a nice Debian/Ubuntu feature to install all the source dependencies required like this:

```
sudo apt-get build-dep k3b
```

I'm running Kubuntu 19.04 and even on this machine, that would install over a hundred new packages.

Then you'd have to download the K3b source and build it.

Frankly, I'd just install Kubuntu 18.04.

---

### Post by Ralph L on 2019-07-23
Thanks for the responses.  Among other things I am trying to learn more about installing from source, since that usually gives the latest version of things.  

SeijiSensei:  Could you explain how "sudo apt-get build-dep k3b" would know to get the dependencies for K3b version 19.04 and not for some earlier versions of K3b.  K3b 19.0.4 requires KF5 Version 5.48.0 not the earlier versions of KF5.  It would seem to me that I would have to specify K3b 19.0.4 some place in the call.
Just trying to educate myself.

---

### Post by SeijiSensei on 2019-07-23
You might be able to do it by just adding the 19.04 [universe]("https://launchpad.net/ubuntu/+source/k3b") source archive though it might conflict with the other packages on your machine.

```
deb-src http://us.archive.ubuntu.com/ubuntu/ disco universe
```

I'd probably update the entire system to 19.04 first myself rather than trying to muck around with packages that may or may be consistent.  14.04 is [no longer supported]("https://wiki.ubuntu.com/Releases"), though it doesn't reach end of life until 2022.

The real issue is whether the most recent K3b depends on calls to other functions in the libraries that don't exist in their 14.04 versions.  You could try just running "apt-get build-dep" then trying to compile the most recent K3b source. I'm going to guess that won't work given how 19.04 uses KDE5 and 14.04 uses, I believe, KDE4. The Qt libraries are a moving target as well.

---

### Post by Ralph L on 2019-07-25
SeijiSensei:  Thanks for your advice.  I will probably follow it and wait until I upgrade my system.  I usually just run the long term support releases, so it will be a while.  CatKiller gave similar advice.

---

### Post by SeijiSensei on 2019-07-25
> **Ralph L said:**
> SeijiSensei:  Thanks for your advice.  I will probably follow it and wait until I upgrade my system.  I usually just run the long term support releases, so it will be a while.  CatKiller gave similar advice.
Me, too. However I decided to give 19.04 a try because of major changes to KDE's Plasma and so far it has run flawlessly. I'll have to update to 19.10 in the fall before going over to 20.04 next year.

---

