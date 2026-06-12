---
title: "Can't install dvdrip"
date: 2005-10-24
forum: General Help
---

### Post by Nolgthorn on 2005-10-24
Hi, when I used to use the older version of Ubuntu I was able to download and install all of the dependencies and dvdrip itself from synaptic. Now it no longer seems to be fully supported in the repositories, if I am doing something wrong please let me know. I've looked everywhere on these forums for a solution but one has not been found.

I get the following error: dvdrip:
Depends: transcode (>=2:0.6.14) but it is not installable

My sources.list looks like this:```
## Main archive
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

## Security
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse

# Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

# Extra
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Debian-Marillat
# deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

---

### Post by ecobuntu on 2005-10-24
Are you running Hoary or Breezy?  If you're running Breezy it's because you haven't change your repositories.

---

### Post by Nolgthorn on 2005-10-24
According to my "Welcome to Ubuntu Linux" it's version 5.04 : The Hoary Hedgehog Release.

Thanks

---

### Post by Nolgthorn on 2005-10-26
Bump, should I just give up and install Breezy? I would feel better if I knew the upgrade isn't going to be in vein. I tend to lose a lot when I make the upgrade, like my apache settings and such so it is a bit of trouble for me to do so. Any testers.

---

### Post by Nolgthorn on 2005-11-07
I am subscribed to this thread so if you have an answer at any time please post it I will return to the thread to read it for sure. Thanks.

---

### Post by _MiniMe_ on 2005-11-08
I think the best way would be to upgrade to breezy. The installation works with 5.10 (at least it did 2 weeks ago). When I was using Hoary, I also had Problems installing dvd::rip. If you want too keep Hoary, try using

```
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```

as a repository. If you are lucky, it will work and not break your system. When the dependencies still can't be solved, you can still try "sid" marillat. 

Try to use as few packages from marillat as possible. Install all the packages separately. Start with transcode and look what packages (that transcode depends on) can't be installed (without marillat in sources). Then try to install that packages from marillat sarge/testing/sid. Don't forget to remove marillat from your sources after that and "apt-get update"!. 

When transcode is installed, it should be easy to install dvdrip too (from the ubuntu-repos). I hope your system will survive that... 

good luck

---

