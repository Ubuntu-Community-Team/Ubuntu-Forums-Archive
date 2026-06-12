---
title: "Transmission not connected to tracker/not downloading"
date: 2014-02-13
forum: General Help
---

### Post by abdulmajid on 2014-02-13
Hi,

I have a Xubuntu 12.04 installation and tried to download some torrents by transmission but it is not downloading. It says 'could not connect to the tracker. I have checked whether the port is open, it is open. I have ufw disabled and nothing configured in iptables. I also upgraded the transmission but no luck. I have Ubuntu 12.04 which works fine, downloads torrents.

What might be wrong? what else can i do for troubleshooting? I checked other forums and threads in this forum. Could there be a network problem, or router issue?

Thanks in advance

---

### Post by Dave_L on 2014-02-13
What version of Transmission are you using?

The relevant package names are transmission-common and transmission-gtk.

I was using the version that's in the standard repositories for Ubuntu 12.04, but ran into a couple of bugs. I found a PPA with a newer version that fixed the bugs:  [https://launchpad.net/~transmissionbt/+archive/ppa](https://launchpad.net/~transmissionbt/+archive/ppa)

This may not solve your problem, but it could be worth trying.

---

### Post by oldos2er on 2014-02-13
Moved to General Help.

---

### Post by abdulmajid on 2014-02-14
Hi,

I am using the same ppa archive you mentioned and I am running 2.82 (14160) version of transm,ission.

---

### Post by abdulmajid on 2014-02-14
bump

---

### Post by abdulmajid on 2014-02-15
I asked Transmission to use a random port everytime it starts, so it is able to download now.

---

