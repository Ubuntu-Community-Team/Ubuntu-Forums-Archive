---
title: "Why so many updates?"
date: 2012-11-05
forum: General Help
---

### Post by raf-kig on 2012-11-05
I reinstalled Xubuntu 12.04 over my existing Ubuntu 12.04 because I figured that being a scaled-down distro it wouldn't be getting so many updates. Wrong!. Every day I'm getting  updates. So I'm wondering is this "LTS" release of Ubuntu/Xubuntu is so full of security vulnerabilities and/or bug fixes that it needs to be updated daily?

---

### Post by Bucky Ball on 2012-11-05
If you made the disk three months ago, then there are three months worth of updates. 

You can click a couple of boxes during install to update and install third-party software during install from memory, which will avoid updating later by updating then. 

If you want the latest, download the ISO via torrent, burn a disk. Much fewer updates required. ;)

If you reinstall the OS over the old one, nothing remains of the old one. Any updates are obliterated, you are starting from scratch with the release locked in time at whenever your burnt the install CD/USB; back to square when and exactly as when you installed for the first time from that particular CD/USB.

PS: In Software Sources, set it to update once a week. Has nothing to do with 'security vulnerabilities', etc. and it doesn't need to be updated daily. If you want to know *why* it is being updated, taking a look at *what* is being updated.

---

### Post by raf-kig on 2012-11-05
> **Bucky Ball said:**
> If you made the disk three months ago, then there are three months worth of updates. 

You can click a couple of boxes during install to update and install third-party software during install from memory, which will avoid updating later by updating then. 

If you want the latest, download the ISO via torrent, burn a disk. Much fewer updates required. ;)

If you reinstall the OS over the old one, nothing remains of the old one. Any updates are obliterated, you are starting from scratch with the release locked in time at whenever your burnt the install CD/USB.
I installed 12.04.1, and I installed third-party software. All this was done the day after 12.04.1 was released.

---

### Post by FormatSeize on 2012-11-05
I don't have 12.04 in front of me right now to verify this, but I believe that it is set to automatically check for updates daily. There is a way to tell the update manager how often you want it to automatically check for updates, or to tell it not to automatically check for updates at all.

---

### Post by jerome1232 on 2012-11-05
So you're actually *complaining* that bugs are being fixed and security vulnerabilies are being patched to quickly for you?

That's what I call a good problem to have.

---

### Post by Bucky Ball on 2012-11-05
> **Bucky Ball said:**
> If you made the disk three months ago, then there are three months worth of updates.

You made updates to the previous install. Now you have reinstalled over the top of that you are at square one. It makes no difference what you did then. That is gone. Nothing gets saved to the install CD, whether you updated/third-party software installed during install or not. That is saved to the partition which has been wiped when you reinstalled.

**Bottom Line: **Consider this a fresh install, the first Ubuntu install ever on your machine. What has happened in the past is irrelevant. 

> If you want the latest, download the ISO via torrent, burn a disk. Much fewer updates required. ;) @ FormatSeize: Said that. Please read thread, not just first post.

> PS: In Software Sources, set it to update once a week. Has nothing to do with 'security vulnerabilities', etc. and it doesn't need to be updated daily. If you want to know *why* it is being updated, take a look at *what* is being updated.

---

### Post by raf-kig on 2012-11-05
> **FormatSeize said:**
> I don't have 12.04 in front of me right now to verify this, but I believe that it is set to automatically check for updates daily. There is a way to tell the update manager how often you want it to automatically check for updates, or to tell it not to automatically check for updates at all.
Yes I see those options on update manager, but my question remains: Is Ubuntu so full of security vulnerabilities and/or bug fixes that it requires daily updates?

---

### Post by Bucky Ball on 2012-11-05
> **raf-kig said:**
> ... security vulnerabilities and/or bug fixes ... 

Why are you assuming that is what's happening? Again:

If you want to know *why* it is being updated, take a look at *what* is being updated.

You're doing an update so it could be exactly that; updating packages that are working perfectly well already (and securely) but will have a new feature or work more efficiently with a new tweak the devs came up with overnight or after pizza.

Just set it to update once a week. How big are these daily updates? 10Mb? 3? I go once a week for anywhere between 100-250Mb. That is normal, generally is, and I have been using Xubuntu for a few years. Divide my total by seven and see if that matches how much you are getting a day.

For comparison, 10.04 LTS, which has been out for two and a half years, gets very little in the way of updates. You will find after 12.04.4 things will slow down, too. 

It ebbs and flows. There are deadlines for the stages, 12.04.2 say, and stuff sometimes comes rushing in all at once to fit those deadlines then out via updates. There can be other factors, too. ;)

---

### Post by raf-kig on 2012-11-05
> **Bucky Ball said:**
> Why are you assuming that is what's happening? Again:



You're doing and update so it could be exactly that; updating packages that are working perfectly well already (and securely) but will have a new feature or work more efficiently with a new tweak the devs came up with overnight or after pizza.

I did NOT do an update, it was a clean install with mount points at my / and /home partitions. The / partition was reformatted to ext4, /home was not reformatted but was an existing ext4 partition.

---

### Post by QIII on 2012-11-05
I believe what Bucky Ball is trying to tell you is that what you are doing now is applying periodic updates.

"You are doing" is present progressive tense in English.

And yes, there are often a lot of them on some days.  As developers improve things, the packages are updated.

---

### Post by Bucky Ball on 2012-11-05
> **QIII said:**
> I believe what Bucky Ball is trying to tell you is that what you are doing now is applying periodic updates.

And yes, there are often a lot of them on some days.  As developers improve things, the packages are updated.

Yep, just regular daily updates. Set it to weekly if annoying. ;)

---

### Post by critin on 2012-11-05
If you allow it to update daily, you won't get as many--some days none.  Right now, I have 7 waiting to be installed.   Iphone, I PodTouch, etc.

Don't forget, any extra PPAs you've added will also update your  apps.    Look at those and see where the updates are actually coming from.

---

### Post by raf-kig on 2012-11-05
> **Bucky Ball said:**
> Yep, just regular daily updates. Set it to weekly if annoying. ;)

Well, I have to say that it's kind of unnerving that Ubuntu requires more daily security fixes than Windows 7.

---

### Post by Bucky Ball on 2012-11-05
Not sure that you're getting it:

Do an update and look at what's being updated before proceeding. Scroll through them in the GUI. Are they security fixes or just updates to software? The security fixes are clearly marked. There might be a few. 

And again, this time next year or at 12.04.1 things will probably be quiet as a millpond most of the time with the occasional swell of updates.

Frankly, it might help if you did some research on Linux and security. You seem a bit worried that Ubuntu is a leaky bucket with devs constantly attempting to plug the leaks. That is faaaaaaaar from the case (with Ubuntu at least).

Good luck with it all. 

PS: Win 7 has been out a darn sight longer than 12.04 LTS ... how many updates did that get in the first year? What about Win 8 updates?

---

### Post by QIII on 2012-11-05
It's not a matter of "requirement" necessarily.  It's more often continuous development.  You don't have to wait for improvements like you do in Windows.

And there are as many security updates in Windows.  You just get them all in big lumps.  Here, you get them in "real time."

So what do you want?  A security patch after a zero day exploit or as a developer tests and finds things?

Remember that some of those security updates are not to Ubuntu per se, but to the software you have installed.

---

### Post by raf-kig on 2012-11-05
I'm a die-hard Ubuntu fan, always was and always will be. Thanks to  Bucky Ball and QIII for your explanations.

---

### Post by JKyleOKC on 2012-11-05
One other point that neither BuckyBall nor QIII mentioned: The 12.10 initial release just came out in the past 10 days; whenever a new major version is released, there's usually a mini-flood of updates to the previous LTS version to incorporate things that were developed for that newer major version. Most of those which I have seen are reflecting upstream changes, or adding functionality to support things that I don't use, but I install them anyway to keep my systems up to date.

---

### Post by jerome1232 on 2012-11-05
I'm not sure if this was mentioned but another point is Ubuntu update updates every.single.application.installed while Windows update updates Microsoft products only.

---

### Post by SantaFe on 2012-11-06
Hehehe.... updates GOOD! ;)

---

