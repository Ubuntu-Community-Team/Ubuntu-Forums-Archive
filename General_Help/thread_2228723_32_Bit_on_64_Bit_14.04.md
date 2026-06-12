---
title: "32 Bit on 64 Bit 14.04"
date: 2014-06-09
forum: General Help
---

### Post by jeremy-lansman on 2014-06-09
Has it been decided to dump us?  I have taken a lot of time running simple re-installs.  I am now reminded again, as I see this in response to an apt-get update command...
*************
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages](http://za.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.200 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
************
FYI:  My OS was originally installed on a Thank Pad.  It died.  Swapping the HD into a new to me Dell L702X mostly worked, except for a couple of drivers.  At update to 14.04 one fix led to another and ultimately a clean up caused by install over the existing 14.04 off the DVD.  [Let this be a warning, maybe a fresh install, as horrible as that is will be easier].  Most applications were gone.  Now I have to do fresh installs of many programs.  Many are tangled into what i think is a new 32 bit hell hole.  I guess the worst was Google Earth.  I now have an older version working.  Man, what a mess that was... yah... I got it working.  Now, i just finished with Filezilla (I used it a lot, and the log in/pwd stuff is already in there)  I am thinking Ubuntu has intentionally made it more difficult.  Am I wrong?

---

### Post by dragonfly41 on 2014-06-09
I've just had a look at ... [http://za.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/](http://za.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/)

and I believe that you have to add the extension to download (Packages without extension is not found)

[http://za.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages.gz](http://za.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages.gz)

---

### Post by grahammechanical on 2014-06-09
Let me see if I understand correctly what you did. You took the OS/HD from one machine and put it into another machine. Yes? You did this although the second machine had different hardware to the first machine. And as you found out Linux will work when we do that but not perfectly. Then, you upgrade (12.04 was it?) to 14.04 but you did not remove non-default software such as google earth. And you did not expect problems.

It is not Ubuntu that has intentionally made it more difficult it is you by expecting too much from an upgrade. The upgrade process is designed for a default install of Ubuntu. How could it be otherwise when the developers have no idea of the changes we have made to the OS.

Many of us on this forum recommend a fresh install because we see many reports of upgrades being broken and some common causes, in my opinion, are: proprietary video drivers, installed software that is not in the Ubuntu Software Centre, non-default themes and the present of alternative desktop user interfaces.

We claim the freedom to do what we like to the OS and then we demand that the developers take away all pain from upgrading. And we are using an OS that we have not paid a penny for. We are not disgruntled customers because we are not customers in the first place.

Regards.

---

### Post by jeremy-lansman on 2014-08-07
Hi Grahammechanical.   Yes.  I am too slow to try it the right way!! And how right you are.  In fact I did a all you said I did, and was thrilled it worked at all.  From the forums, learned that hardware drivers are part of the kernel, so probably things will work, as they do when you boot from a live Ubuntu CD. Dependencies for software packages may fail, as libraries change in a version upgrade.  I had to run a serious clean out a couple of months back, and had to re-install a lot of libraries.  It took a lot of time. But less, for me, than a fresh install.  I have an older version of Google Earth and it works well for me.  Mostly, I find that with Ubuntu most things on the L702X work OK.  Under 12.04 HDMI failed.  Under 14.04 LTS HDMI  worked like a charm.  The Dell L702X had a serious wifi problem.  The chip it uses seems to be uncommon enough that it may not be attended to.  To use the WIFI I tried a prerelease kernel and got things working.  Then post 14.04 LTS install wifi worked fine. 

That is until a few days ago, when something changed...   well, if I wanted to write a driver to contribute to Ubuntu, I could learn how and do it.  So this is hardly a complaint.   Yes, it is time I do a proper fresh install.  A new HD will allow it combined with several days spare time, as I have a whole lot living inside this incredible Ubuntu's 135 GB space. A fresh install is proper.

It would be nice if South African ISPs would allow free (not metered,,,it is local after all) download from Ubuntu repositories.  Doing a fresh install of everything used a lot of internet resource which here in rural SA is so easy to come by.

---

### Post by jeremy-lansman on 2014-08-12
Graham:  I did a fresh 14.14 LTS install.  Wifi worked reliably.  I did an update.  Wifi fails.  I think this is good evidence someone broke the L702x wifi driver.

---

### Post by whitesmith on 2014-08-12
> **grahammechanical said:**
> Let me see if I understand . . . Regards.
++10 A perfect restatement of what is said on the initial webpage in my signature line. You have my thoughtful regards.

---

