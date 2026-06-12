---
title: "Compiz does not work on Hardy Heron"
date: 2008-05-12
forum: General Help
---

### Post by Galactic Jack on 2008-05-12
I figure this has to do with the driver on my videocard - but how do I find out what video card I have and that driver I would need for it?

What command do I type to list my hardware profile?

---

### Post by tamoneya on 2008-05-12
type ```
sudo lspci
```and post the output here.

---

### Post by Rocket2DMn on 2008-05-13
To just see your video card, run
```
lspci | grep VGA
```
sudo is not necessary for lspci in Ubuntu (though it is in some linux distributions for this command).
If it says your video card is ATI and it is older than a Radeon 9500, have a look here - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by undfined on 2008-05-13
I've got compiz working with the latest nVidia drivers under Hardy - and am pretty happy with it.

You can do a search here or at google after you know what video card you have, to find out its usability - or quirks.  Good luck.

---

### Post by Galactic Jack on 2008-05-14
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

---

### Post by Kevbert on 2008-05-14
Please check out this link: [http://ubuntuforums.org/showthread.php?t=678211]("http://ubuntuforums.org/showthread.php?t=678211")

---

### Post by Galactic Jack on 2008-05-14
You link only has drivers posted up to Ubuntu 7.10. I.E. It won't let me install any of them

---

### Post by CrazyArcher on 2008-05-14
> **Galactic Jack said:**
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

Hrm, I have the same adapter, and I thought that it's not strong enough to run Compiz. Did it work on earlier Ubuntu versions/other distros? If yes, what are your overall system specs?

---

### Post by Galactic Jack on 2008-05-14
I've never tried this before on my desktop. But this is lame. I'm gonnah ave to go out and buy a whole new video card. Meh I'll probably just scrap the PC as a whole anyways once solid state drives become bigger and cheaper

---

### Post by docamo on 2008-05-14
> **CrazyArcher said:**
> Hrm, I have the same adapter, and I thought that it's not strong enough to run Compiz. Did it work on earlier Ubuntu versions/other distros? If yes, what are your overall system specs?

I am also having trouble with compiz. This is what I got when I entered lspci | grep VGA. For the first two days it was working but has not since.

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

---

### Post by Kevbert on 2008-05-14
> **Galactic Jack said:**
> I've never tried this before on my desktop. But this is lame. I'm gonnah ave to go out and buy a whole new video card. Meh I'll probably just scrap the PC as a whole anyways once solid state drives become bigger and cheaper

Are you using display drivers which came with Ubuntu or restricted drivers ?
Also whats the highest resolution that you can display in Ubuntu ? (1024x768 ?)

---

### Post by Rocket2DMn on 2008-05-14
> **Galactic Jack said:**
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

OK you don't have a standard ATI or NVIDIA card.  You will be using one of the less known drivers that is more specific to your model of card.  I don't recall exactly what the driver is called, probably something like "s3".  It is unlikely that you will be able to use compiz with this card.

---

### Post by CrazyArcher on 2008-05-14
It's not even a card, it's an onboard chip that leeches memory from RAM, not having his own (64MB). It's pretty good for a pathetic thing like this, however: I was able to run stuff like UT2004 pretty good on it. Yet, it has its limits.

---

### Post by docamo on 2008-05-14
I have just reinstalled compiz and it is still not working? I am still getting the message "Visual effects could not be enabled." Any suggestions?

---

### Post by Kevbert on 2008-05-14
Just found a link on Compiz-fusion website [http://forum.compiz-fusion.org/showthread.php?t=5691]("http://forum.compiz-fusion.org/showthread.php?t=5691").  S3 will not run Compiz.

---

