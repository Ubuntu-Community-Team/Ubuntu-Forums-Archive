---
title: "New install process is horrible"
date: 2006-07-23
forum: General Help
---

### Post by krishnabobby on 2006-07-23
The ive-CD only version of ubuntu is making me reconsider standardizing on Ubuntu.:(  On one 2GHz PC, I spent several hours trying to cope with the delays associated with the live-CD-ness of it only to have it lock up or otherwise fail miserably. You just put yourselves back in the Knoppix-lookalike category; I ended up using Knoppix on that machine instead. Their hd-install isn't great,:rolleyes:  but it's a LOT more reliable than this one - and at least they have no real pretensions of being an installable Linux. Maybe you should put a warning label on it "Not for older machines or CD drives." :-k

---

### Post by ciscosurfer on 2006-07-23
You should try [Xubuntu]("http://www.xubuntu.org/") (uses Xfce as the wm) if you've got an older machine.

---

### Post by Jagot on 2006-07-23
It should not take several hours - Did you checksum the disk?

---

### Post by ciscosurfer on 2006-07-23
us.archive.ubuntu.com is having problems right now...and so installing / updating your system will either fail completely or be very, very slow.  Try back tomorrow or later today.

---

### Post by woopud on 2006-07-23
> **krishnabobby said:**
> The ive-CD only version of ubuntu is making me reconsider standardizing on Ubuntu.:(  On one 2GHz PC, I spent several hours trying to cope with the delays associated with the live-CD-ness of it only to have it lock up or otherwise fail miserably. You just put yourselves back in the Knoppix-lookalike category; I ended up using Knoppix on that machine instead. Their hd-install isn't great,:rolleyes:  but it's a LOT more reliable than this one - and at least they have no real pretensions of being an installable Linux. Maybe you should put a warning label on it "Not for older machines or CD drives." :-k

(one 2GHz PC)  "Not for older machines"  ???  you guys need to get serious, since when is a 2ghz PC an older machine ?  I'm running Dapper on a P3, 733 mhz everything works flawless don't need xubuntu.

Bert

---

### Post by ciscosurfer on 2006-07-23
us.archive.ubuntu.com is down...that's why he was having issues

---

### Post by Jagot on 2006-07-23
> **ciscosurfer said:**
> us.archive.ubuntu.com is down...that's why he was having issues

I don't think it is.  The install CD can take most files it needs from the install CD.  I suspect there's a problem with the disk itself.

---

### Post by blitzd on 2006-07-23
> **krishnabobby said:**
> The ive-CD only version of ubuntu is making me reconsider standardizing on Ubuntu.:(  On one 2GHz PC, I spent several hours trying to cope with the delays associated with the live-CD-ness of it only to have it lock up or otherwise fail miserably. You just put yourselves back in the Knoppix-lookalike category; I ended up using Knoppix on that machine instead. Their hd-install isn't great,:rolleyes:  but it's a LOT more reliable than this one - and at least they have no real pretensions of being an installable Linux. Maybe you should put a warning label on it "Not for older machines or CD drives." :-k

I've installed Dapper on my Core Duo 2 GHz laptop in less than 10 mins from the moment I switched it on. Fastest Linux install I have seen yet on it, in fact. I've also installed it on my 1.2 GHz desktop (at least 4 years old) and it flew through that as well. Maybe you've got a bad CD, or maybe your CD drive just doesn't like that CD - lot's of older drives can be touchy about certain burnt discs.

I don't think the repositories would have an effect on the actual install, it doesn't hit the repos until after the install/reboot to update. And even then if the repos don't respond you don't get a message to update anyways.

---

### Post by lapsey on 2006-07-23
try the "alternative" CD. Just as it ever was.

---

### Post by JoWilly on 2006-07-23
As was said previously, you most certainly have errors on your disk.

---

### Post by az on 2006-07-23
> **krishnabobby said:**
> The ive-CD only version of ubuntu is making me reconsider standardizing on Ubuntu.:(  On one 2GHz PC, I spent several hours trying to cope with the delays associated with the live-CD-ness of it only to have it lock up or otherwise fail miserably. 

What delays associated with the live cd?  It takes about a minute longer to boot and depending on your ram, can be a little slower.  Anything measured in hours is certainly not normal, don't you think?

> **krishnabobby said:**
>   Maybe you should put a warning label on it "Not for older machines or CD drives." :-k


I have installed using Ubiquity (the live cd installer) on a pentium II 333MHz with an 8x cdrom drive and a teeny tiny 2 gig hard drive.

---

### Post by ciscosurfer on 2006-08-05
> **blitzd said:**
> I don't think the repositories would have an effect on the actual install, it doesn't hit the repos until after the install/reboot to update. And even then if the repos don't respond you don't get a message to update anyways.

In fact, provided you have a live internet connection, the **security-updates repo** *does get hit* when installing from the Live-CD (I just reconfirmed this) and so it very well could've taken a very long time to install had the repo been down (as it was).  A quick solution to this problem would be to simply unplug your ethernet until the install in complete.  Once rebooted, you can change the repo to one that isn't down, and complete the install that way (along with a slew of other updates that present themselves upon new install/reboot).

---

### Post by bigaltx on 2006-08-06
I had the same problem when trying to install Dapper on a 1.2gig processor. MD5SUM was ok, wound up burning another CD on a different brand of CD. With a good CD install was very quick and easy.

---

### Post by orb9220 on 2006-08-06
Must be just did a reinstall last night on 1.3 P4 with 640mb of ram.
Boot to live desktop  5 mins.
             Install 40 mins.
    Donload upgrades 22 mins. 156 packages of 184mb @ 130Kb/s
   Applying upgrades 11 mins.
 Easy Ubuntu upgrade 12 mins.
             reboot and the total is 90 mins.

So even a slower system with less ram I would start to worry at the 1 hr mark for just the basic install.

---

### Post by hazart on 2006-08-06
I have experienced the same delays. 10 min to boot, and about 20 minutes for the install app to launch and show the first language page. The reason was bad cd-quality. It was a CD-RW in an old drive.:mad: 

I ordered the Dapper Drake cd's from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) and now the install works flawless, and is very fast.

I cant stress enough how important a good CD-quality is to the install process. I've seen lots og computes choking on the cd, and not even booting, because of the cd! :-?

---

### Post by dalee on 2006-08-06
Hi,

I too think you've got a "bad" disc or burn. And like Bigaltx, I too had a problem with Dapper final just last month when a hard drive crashed and burned on me:twisted: . I downloaded the final on my other box and burned a CD. Check sumed correctly and appeared to be good, but just wouldn't install. Just hung about halfway through during three seperate attemps.

I finally just used my last Dapper flight CD, and it installed fine. Just had to do apt-get distro upgrade to finish.

dalee

---

### Post by orb9220 on 2006-08-06
And DO NOT use Cd-RW's even in the windows world of video production they  are not trusted.

And when you get a good burn amd go back to it a month or few down the road it has gone bad.

At least that has been my experience.

---

