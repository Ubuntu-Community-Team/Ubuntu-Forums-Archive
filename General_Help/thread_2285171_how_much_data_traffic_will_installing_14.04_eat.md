---
title: "how much data traffic will installing 14.04 eat?"
date: 2015-07-03
forum: General Help
---

### Post by t0p on 2015-07-03
I've decided to install Ubuntu (next to Windows 8). USB up n ready to go.  I'm running low on data allowance. Will 800MB be enough for the stuff I will need pronto (vlc, flash, etc)?  800MB is plenty enough for this stuff, right?  right?

---

### Post by tgalati4 on 2015-07-03
Unless you know what you are doing, most installs are over 1 GB, which is why CD's are no longer offered.  Perhaps look for a local Linux User's Group and see if anyone has a recent DVD.  Install with that, then 800 MB will be enough to perform the first round of updates.

What city are you in?  I'm sure you have someone close with extra disks.

---

### Post by howefield on 2015-07-03
Depends on what exactly "ect" means and how much of your 800 you want left at the end :)

Without counting updates or additional drivers, all the packages I download after a fresh install come to about 280 MB - probably about 80MB of that for the "pronto" stuff. You most likely know that using the terminal to apt-get your packages will tell you how large the download will be, likewise synaptic and probably other methods too.

---

### Post by grahammechanical on 2015-07-03
My suggestion would be to wait until 6th August and then download Ubuntu 14.04.3. The image available at present is 14.04.2 but the 14.04.3 image will include all the updates that have been made since 14.04.2 was released in February.

If you cannot wait that long you can download a Trusty (14.04) daily built image.

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

If you already have a 14.04 ISO image on the hard disk you can use zsync which will only download the difference between that 14.04 ISO image that you already have and the newest daily ISO image.

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/97160/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/97160/downloads)

If you do not have an existing ISO image then the zsync command will download the full ISO image.

When installing do not tick to install updates at the same time. Do not tick to install third party software. That will reduce the data downloaded during the installation.  You can also disconnect from the internet and see what happens. Everything should be installed from the DVD/USB stick.

After installation Software Updater will allow us to untick those updates we want to delay being installed.

Regards.

---

### Post by t0p on 2015-07-04
Thanks very much to everyone who replied.  I think I'm going to wait for 14.04.3.  August isn't that far away, I reckon I can carry on using my old wreck of a machine til then.  And it really is a wreck of a machine!  I accidentally broke the screen when I stupidly left the laptop on the floor (dumb move, never gonna do *that* again)... I spilt rather a lot of beer on it, so the keyboard and trackpad mousey thing doesn't work... I'm surprised the computer still works!  But it means I'm tied to a monitor and usb keyboard and mouse - so the laptop is a desktop.  Windows scares me, as unwanted tabs open on my browser all the time, and Avast continually tells me unwanted programs have been detected (no need to panic, Avast has "dealt with it", but it happens all the time.  I think it's cos I'm using Avast's free version and this is their way of getting folks to go for their paid-for version).

I really miss the laptop experience.  But I can wait til August.  Has a date been announced for the release of 14.04.3 yet?

**EDIT:** There I go again, asking questions then finding the answer for myself.  [14.04.3 is scheduled for release on 6th of August]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule").  Anyway, thanks guys.

---

### Post by howefield on 2015-07-04
> **t0p said:**
> ...Has a date been announced for the release of 14.04.3 yet?

As said above, August 6th looks likely :)

[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

---

