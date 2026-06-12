---
title: "Update manager not working!!"
date: 2008-06-18
forum: General Help
---

### Post by beckols on 2008-06-18
I'm currently on gutsy, and I'm having trouble with my update manager.  If I click Upgrade so I can get Hardy, update manager freezes up and stops responding.  When I click Check, it says it's downloading 36 updates, but then none show up in the update box.  What's going on??  I've tried from command line as well:
apt-get update
apt-get upgrade
apt-get dist-upgrade

nothing works!!

---

### Post by rraj.be on 2008-06-18
> **beckols said:**
> 
apt-get update
apt-get upgrade

nothing works!!

could you just post me the output that you got in the anyof the above command.

---

### Post by beckols on 2008-06-18
apt-get update

```
colin@colin-ubuntu:/etc/apt$ sudo apt-get update

[sudo] password for colin:

Get:1 http://packages.medibuntu.org hardy Release.gpg [189B]

Ign http://packages.medibuntu.org hardy/free Translation-en_US

Ign http://packages.medibuntu.org hardy/non-free Translation-en_US

Hit http://packages.medibuntu.org hardy Release

Hit http://packages.medibuntu.org hardy/free Packages

Hit http://packages.medibuntu.org hardy/non-free Packages

Get:2 http://mirror.cc.columbia.edu gutsy Release.gpg [191B]                   

Ign http://mirror.cc.columbia.edu gutsy/main Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy/restricted Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy/universe Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy/multiverse Translation-en_US

Get:3 http://mirror.cc.columbia.edu gutsy-updates Release.gpg [191B]

Ign http://mirror.cc.columbia.edu gutsy-updates/main Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy-updates/restricted Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy-updates/universe Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy-updates/multiverse Translation-en_US

Get:4 http://mirror.cc.columbia.edu gutsy-security Release.gpg [191B]

Ign http://mirror.cc.columbia.edu gutsy-security/main Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy-security/restricted Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy-security/universe Translation-en_US

Ign http://mirror.cc.columbia.edu gutsy-security/multiverse Translation-en_US

Hit http://mirror.cc.columbia.edu gutsy Release

Hit http://mirror.cc.columbia.edu gutsy-updates Release

Hit http://mirror.cc.columbia.edu gutsy-security Release

Hit http://mirror.cc.columbia.edu gutsy/main Packages

Hit http://mirror.cc.columbia.edu gutsy/restricted Packages

Hit http://mirror.cc.columbia.edu gutsy/universe Packages

Hit http://mirror.cc.columbia.edu gutsy/multiverse Packages

Hit http://mirror.cc.columbia.edu gutsy-updates/main Packages

Hit http://mirror.cc.columbia.edu gutsy-updates/restricted Packages

Hit http://mirror.cc.columbia.edu gutsy-updates/universe Packages

Hit http://mirror.cc.columbia.edu gutsy-updates/multiverse Packages

Hit http://mirror.cc.columbia.edu gutsy-security/main Packages

Hit http://mirror.cc.columbia.edu gutsy-security/restricted Packages

Hit http://mirror.cc.columbia.edu gutsy-security/universe Packages

Hit http://mirror.cc.columbia.edu gutsy-security/multiverse Packages

Fetched 4B in 13s (0B/s)

Reading package lists... Done

```

apt-get upgrade

```
colin@colin-ubuntu:/etc/apt$ sudo apt-get upgrade

Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

colin@colin-ubuntu:/etc/apt$ 
```

---

### Post by avtolle on 2008-06-18
Is the mirror down? Could you, in software sources, select the Main server or the U.S. server, reload and try again?

---

### Post by beckols on 2008-06-18
I just tried switching to both the US server and the main server, and neither worked

---

### Post by beckols on 2008-06-18
Ok, well I did this:
do-release-upgrade

and it magically started downloading a bunch of things, but not hardy updates.

Right before it prompted me to start downloading the hardy upgrade, I had a feeling it fixed the update-manager and sure enough I checked it, and there were 332 updates ready for download!!  I don't know what happened, could anyone kindly inform me?

---

### Post by Tim.Read on 2008-06-18
Hi All,

I'm having very odd behaviour from from Synaptic Package Manager, Update Manager & apt....

apt works...
Updates Manager shows updates but won't install them...
Synaptic Package Manager shows packages as "local & obsolete"

How can this be?

---

