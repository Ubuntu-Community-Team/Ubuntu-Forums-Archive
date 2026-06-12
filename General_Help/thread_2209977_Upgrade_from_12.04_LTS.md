---
title: "Upgrade from 12.04 LTS ?"
date: 2014-03-08
forum: General Help
---

### Post by sarahfoxnz on 2014-03-08
Hello.

1) I've got - Release 12.04 (precise) 64-bit

I regularly update it, every few days. & get 50-100MB of downloads of updated stuff.

query: is there an upgrade to 12.04 LTS ? & how will i know when opne is released ?

2) Sometimes (not always - but more regular than not), i get a red triangle at the top right of my screen saying my system updates havn't been done in 180+days, or the package details etc (i can't remember exact words). I think its something wrong with the URL / storage area my PC is updating from.

i update frequently, & shouldn't be seeing  such a message.

Query: How do i know my PC is accessing the correct URL / place for updates ? & if its incorrect, how do i change it / find out where the correct URL is ?.

I did an update just yesterday. Tonight i saw the red triangle & did another update. now the red triangle is gone.

---

### Post by OrangeCrate on 2014-03-08
> **sarahfoxnz said:**
> Hello.

1) I've got - Release 12.04 (precise) 64-bit

I regularly update it, every few days. & get 50-100MB of downloads of updated stuff.

**query: is there an upgrade to 12.04 LTS ? & how will i know when opne is released ?**

2) Sometimes (not always - but more regular than not), i get a red triangle at the top right of my screen saying my system updates havn't been done in 180+days, or the package details etc (i can't remember exact words). I think its something wrong with the URL / storage area my PC is updating from.

i update frequently, & shouldn't be seeing  such a message.

Query: How do i know my PC is accessing the correct URL / place for updates ? & if its incorrect, how do i change it / find out where the correct URL is ?.

I did an update just yesterday. Tonight i saw the red triangle & did another update. now the red triangle is gone.

You are referring to an upgrade to the next LTS, which will be 14.04, right? If so, yes, shortly after release you will get a notice that an upgrade is available from software updates. LTSs are preset to notify on upgrades to new LTS versions only, if I remember correctly, not interim versions like 12.10, 13.04, and 13.10. That's probably why you haven't seen any version upgrades to this point. Right now, you're just doing software updates. When the new version is available, it will tell you exactly that - A new version is available.

---

### Post by TheFu on 2014-03-08
You are doing the right stuff, probably.  There are different sorts of updates and I can't tell what sort you are actually doing.

I update weekly for servers and desktops. Any more often than that and it becomes a chore. I've disabled all nags in GUIs too.  Sometimes, like right before I leave the country, I will NOT do an update. Stability while I'm away is more important than *new*.
Every Saturday morning, I run:
```
sudo aptitude update
sudo aptitude full-upgrade
```

**Aptitude** is like apt-get, but smarter. It handles dependencies that can be more complex. It has been recommended for Debian 5+ yrs. Since Ubuntu is based on Debian ... Apitutude is CLI and already on your box.

**full-upgrade** will upgrade the kernel within the same line, not just provide security patches like the plain **upgrade** does. It will not do a release-upgrade or push a different kernel level.

When I ask my 12.04 systems which kernel they are running (using Ansible), here's the response:
```
xmbc | success | rc=0 >>
3.11.0-15-generic

redmine | success | rc=0 >>
3.2.0-60-generic

qbe | success | rc=0 >>
3.2.0-60-generic

xen41 | success | rc=0 >>
3.2.0-60-generic

netbook | success | rc=0 >>
3.2.0-59-generic-pae

spamcache | success | rc=0 >>
3.2.0-60-virtual

hadar | success | rc=0 >>
3.8.0-36-generic
```
So - most of these systems are running 3.2.0-60-something. Two were installed since 12.04.0 was released, so they have newer kernels; 3.8.xx and 3.11.xx was installed recently. These are all 12.04.4 systems.  Oh ... and I see that I missed rebooting one of the machines this morning  - it isn't running the newer 3.2.0-60 kernel. Need to get on that.

I don't plan to upgrade to 14.04 until **late May 2014** at the earliest.  Running the newest code isn't always good, especially for end-users. Heck, I wish most developers didn't run the newest code too so we'd have greater stability with the LTS released packages and still get updates. 

So - keep doing what you are doing, create good backups at least weekly, and be happy running a system that makes updates relatively easy. ;)  [Systems Maintenance for Ubuntu Desktops]("http://blog.jdpfu.com/linsysmaint").

---

### Post by raja.genupula on 2014-03-08
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

