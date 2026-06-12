---
title: "Where is the GProFTPd repository?"
date: 2007-02-06
forum: General Help
---

### Post by transistor on 2007-02-06
This is probably really dumb but I've wasted a lot of time trying to figure it out.

I'm trying to install gproftpd. Synaptic can't find it. 
"sudo apt-get install gproftpd" can't find it. (I presume they're using the same repositories.)

Here's my /etc/apt/sources.list
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

"apt-get update" gets 17 files without problems but still no joy with gproftpd.

One possible problem: I'm on a corporate network and they may be blocking access to some sites. How would I see which ones are failing?

Many thanks.

---

