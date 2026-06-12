---
title: "Dapper (Gnome): uploading with samba causes freeze"
date: 2007-05-26
forum: General Help
---

### Post by jewishj on 2007-05-26
I have a machine here running Dapper which I use as a fileserver/web server (local intranet for development only).  It worked great from the install time which was just after Dapper was released until about three months ago.  At that time, transfers to and from the machine from other machines (over Samba shares) became very slow (25 min or so to transfer a 300MB file slow, and the LAN is using gigabit switches, cat6 cabling, etc.).

At first, I thought something was jamming up the network and that maybe my roomates machine had gotten a virus or something, but after much investigation - I found this to not be the case.  Strangely enough though, I found that if I would power cycle all the switches and the router, everything would work normally for a brief time again.  Nothing else would be slowed down ever though, download/upload speeds to the web, browsing, etc. would all be normal.  In addition, this didn't seem to be as much of a problem when I was moving files from a Windows machine (my main machine was using Dapper at the time as well) - I would even resort to moving files from inside Windows via VMWare to increase transfer speeds - so I figured that I probably needed to rebuild my main machine (this was my first linux build on my primary machine - and I had messed some things up early on which probably got worse after updates and such - the network thing was not the only thing acting weird on that build).

Recently, I got some hardware upgrades and decided that it would be a great time to rebuild the machine since feisty had just been released also.  So, I rebuilt my main machine, it has a new mb/processor/ram/vid card and is now running Feisty.

The problems with file transfers seem to have only gotten worse.  Now what I find is that transferring from the fileserver to my main machine (or other machines on the network) takes really long - but it will complete successfully.  However, when transferring to the fileserver, it will transfer for a few min or so and then the estimated time on the transfer will keep increasing until it freezes altogether.  Inspecting the fileserver when this happens shows that it either completely freezes (ie. mouse doesnt move, keyboard doesnt respond, etc.) or has automatically restarted or powered off completely.  Also, Windows machines no longer have a transfer speed advantage over my (now) Feisty machine.

This freezing issue only seems to occur with bigger files (about 180MB or more).  I have tried reinstalling samba and all of its counterparts and this did not change anything.

Thanks in advance for any help which you can offer

---

### Post by sparrowkc on 2008-06-13
Still a problem as of June 2008.  I can't transfer large files over samba.

---

### Post by haberb on 2008-06-26
I have been bitten by this as well.

---

