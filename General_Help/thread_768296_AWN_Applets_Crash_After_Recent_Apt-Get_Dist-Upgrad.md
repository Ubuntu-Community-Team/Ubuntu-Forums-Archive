---
title: "AWN Applets Crash After Recent Apt-Get Dist-Upgrade"
date: 2008-04-26
forum: General Help
---

### Post by EmyrB on 2008-04-26
Hi All

Just wandering if anybody else had this issue. I have been using Hardy since about February of this year and until today I have had no issues with it. I have AWN installed and this morning I did the usual apt-get update and then apt-get dist-upgrade and the only thing it listed was an update to awn-core-bzr and awn-lib (I think) it also removed awn-manager.

Since the upgrade everytime I log in I get weird icons in AWN and then applets start crashing like crazy, eg stacks, affinity search, log out, weather applet and digital clock.

Any ideas? Is this an ubuntu issue or an AWN one?

Cheers

EmyrB

---

### Post by Zorael on 2008-04-26
This is likely due to conflicting remnants of the old version, but I couldn't say for sure. I'd try reinstalling awn.

Find the packages in Synaptic (*all* the relevant ones), and make sure to pick **complete removal**.

Don't forget libawn0 and python-awn. :>

---

### Post by EmyrB on 2008-04-26
Cheers for that Zorael but I went into synaptics and I seem to have the bzr versions (3.1) installed the ones without bzr are all like 2.1. Is this correct?

Cheers

EmyrB

---

### Post by Zorael on 2008-04-26
As mentioned, the issue likely stems in version inconsistencies between libraries and the app itself.

The packages you mention (bzr ones) don't seem to exist in the official repositories, so you likely have foreign ones added to your Software Sources. :>

This may (will) mess things up when you mix remnants of them with ones in the Hardy repos. Make sure to disable them in Software Sources (or as lines in /etc/apt/sources.list, or as files ending in .list in /etc/apt/sources.list.d), then reinstall awn.

I never used it myself, but I imagine the packages needed are avant-window-navigator and awn-manager.

---

### Post by EmyrB on 2008-04-26
I hear you :D

I checked my sources.list and this was at the bottom of that file: -

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

As far as I can tell they have been there from day one when I installed Hardy and I think that they are the official (don't quote me on this mind) repo's for AWN.

Any way I will remove all the AWN stuff and do a reinstall.

I shall let you know

Cheers

EmyrB

---

### Post by Zorael on 2008-04-26
I'm not trying to zealously enforce sole use of official repos, but if you get it working with the build available from there, at least you have something to fall back to if you later try other repo packages and they end up breaking stuff. :>

---

### Post by EmyrB on 2008-04-27
Thanks for all the help Zorael, but I still had issues when I downloaded the AWN without the BZR. Anyways, I removed AWN, and then this morning I decided to give the BZR's another try and it now works fine. I checked the file versions and they are different from yesterday, so there must have been something broke in the packages yesterday.

Cheers

EmyrB

---

### Post by gareth9 on 2008-04-27
Firstly,I also had the same problem. I could not even open up preferences,I did all the steps to reinstall awn. I can now see my prefernces and all my applets but when I restart my pc it does not seem to want to start up. I dont see ant awn bars nothing. The only thing that I can access is the preference in System>preferences>Awn Manager. Emyrb maybe you could let me know exactly all the insatlls you selected from Synaptic Package Manger. 
Any help would be greatly appreciated.  Thanks

---

### Post by gareth9 on 2008-04-27
Firstly,I also had the same problem. I could not even open up preferences,I did all the steps to reinstall awn. I can now see my preferences and all my applets but when I restart my pc it does not seem to want to start up. I dont see ant awn bars nothing. The only thing that I can access is the preference in System>preferences>Awn Manager. Emyrb maybe you could let me know exactly all the installs you selected from Synaptic Package Manger. 
Any help would be greatly appreciated.  Thanks

---

### Post by MountainX on 2008-04-30
I am running AWN with Hardy too. The "official" version of AWN in the Ubuntu repos does not support the applets package -- the awn-extras is not available through the repository. Therefore, the best way to get the applets is to use the bzr (reacocard) version. See [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363) 

The source lines mentioned by EmyrB are for the bzr/reacocard version:
```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

(There is one other choice besides reacocard, but the last time I looked about a week ago it was broken temporarily so reacocard's is the only good choice.)

I have been using reacocard's version since I started using Hardy a couple months ago. A couple days ago update manager offered me a partial upgrade choice due to the need to uninstall awn-related packages. Here is what Synaptic is telling me now:
--not authenticated:
libawn-bzr 
--To Be Removed:
python-libawn-bzr
awn-manager-bzr
avant-window-navigator-bzr

In my case I do not have any remnants of other versions of AWN installed. I can say for sure that package conflicts have nothing to do with the current issue.

However, I have not proceeded with the upgrade yet. I thought I would ask if anyone else has additional info first. Thanks.

---

### Post by MountainX on 2008-04-30
I think the problem described in this thread might be due to awn packages being renamed. See this post:

[http://ubuntuforums.org/showpost.php?p=4830586&postcount=84](http://ubuntuforums.org/showpost.php?p=4830586&postcount=84)

---

