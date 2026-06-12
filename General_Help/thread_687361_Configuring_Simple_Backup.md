---
title: "Configuring Simple Backup"
date: 2008-02-04
forum: General Help
---

### Post by wheezer on 2008-02-04
Now that I have 2 weeks worth of Gutsy configured with everything I like, I'd like to keep a pure backup that makes it as easy as possible to upgrade nexttime, getting most of my key applications at least workable, and all my data, but without all the extraneous packages and screw-ups that a daily backup might have, should I decide to do a fairly junk-free rebuild or upgrade.  I am still a noob to linux, so backup strategies still confuse me.

Simple backup's includes are these:
/var/
/home/
/usr/local/
/etc/


Is this  adequate? Don't some applications use /opt/, /usr/share, usr/bin, etc?

Can someone suggest others that should be included, to keep the most useful, restorable version of my entire system, for this "pure" restore?

I'm sure other noobs could benefit from such a response. I couldn't; find one. Thanks in advance.

---

### Post by ajgreeny on 2008-02-04
I don't think there is any real reason to include any other sections of your current install.  To be perfectly honest, I, like most people would only really bother to keep a backup of my home folder, which in my case contains the iso from aptoncd that I run every so often, so that when it comes to reinstalling or helping others install there is no need to download hundreds of MBs of upgrades and additional packages; they will all be in the iso file.  I also have a copy of my sources.list file in a backup folder so I know that will work OK.  The danger if you include too much else is that you will  also just replicate the things that make you reinstall in the first place.

---

### Post by wheezer on 2008-02-04
"contains the iso from aptoncd"

You've lost me already. Not familiar with aptoncd.

---

### Post by zvacet on 2008-02-04
Read [this](http://aptoncd.sourceforge.net/).You can install it from synaptic.

---

### Post by wheezer on 2008-02-04
> **zvacet said:**
> Read [this]("http://aptoncd.sourceforge.net/").You can install it from synaptic.



It looks like no activity there in about a year. Is it stable on Gutsy?

---

### Post by ajgreeny on 2008-02-04
Sure is!  I've used it several times without a single problem.  Lets face it, it's not a very high tech bit of software just to copy the contents of /var/cache/apt/archives to a CD via an iso file.  Go get, it's worth it.

---

