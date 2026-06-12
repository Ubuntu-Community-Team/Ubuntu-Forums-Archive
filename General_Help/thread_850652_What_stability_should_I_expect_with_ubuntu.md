---
title: "What stability should I expect with ubuntu?"
date: 2008-07-05
forum: General Help
---

### Post by TonyGould on 2008-07-05
Hi,

I'm fairly new to ubuntu, and to linux (although I'm not new to computing). My question is, what level of stability should I expect from an ubuntu release?

I have installed 8.04 on 3 machines (2 laptops and a mythbuntu box), all of which had 7.10 on them previously. Broadly, more hardware is recognised automatically and much more easily than on 7.10, and things are more attractive, but unfortunately on one of the machines I have experienced random hangs with no obvious pattern or error logging in /var/log, which need a manual power off/on (other threads go into this in detail, I don't propose to here). On one of the other machines, wireless support which worked flawlessly in 7.10 once I had compiled up ndiswrapper is now much flakier.

I'm not trying to whine; indeed I'm happy to have moved over to ubuntu and grateful it's there and the community support in particular is excellent. I've just moved my whole desktop at home from Windows to Ubuntu, and it rocks -- I was particularly pleased Thunderbird even shares its data across the dual boot with Windows, but haven't actually felt the need to log back into Windows since transferring my Outlook messages across and setting it up :)

My question is, what level of stability and reliability should we reasonably expect? My understanding isn't perfect, but I hear for example that ubuntu is based not on the stable debian but on an "unstable" debian release, so if I really wanted rock solid stability I wouldn't use ubuntu, right? (I'm not looking for flames here, just asking a question.) Indeed, we don't run ubuntu at work to host our web servers; rather we use Red Hat if I remember rightly, and we sure as heck don't roll out new releases every 6 months. Was I naive to have thought I could use 8.04 as essentially a server to record TV (in hindsight I'd have been better off sticking with 7.10 and upgrading just the mythtv bit).

Also, I think I've fallen into the trap of upgrading to Hardy thinking that LTS means that it's going to be higher quality than 7.10 immediately, but have I made a mistake there? I've seen elswhere that LTS means that it's going to be supported long term, but doesn't necessarily mean that it will be more stable from the get go?

Should I just be going for the .10 releases for example? Or once I have something working, stick with it, because the combinations of hardware and software are just too scary and too time consuming?

All comments welcome, and I hope my question can be taken as the open question that it is.

Tony.

---

### Post by dcstar on 2008-07-05
> **TonyGould said:**
> 
..........
All comments welcome, and I hope my question can be taken as the open question that it is.


Any new release of any software is inherently less "stable" than something older, because it will have new and changed features that will always require time to sort out any of the issues that invariably arise.

If you want a "stable" platform of any OS release, wait 6 months after the release date before using it so most of the issues are (hopefully) resolved by then.

This is basic common sense that applies to virtually all software.

And to answer the title question, you should "expect" a new release of Ubuntu to have the same "stability" as any other software release, it will improve as time passes after release date and issues are resolved.

---

### Post by msrinath80 on 2008-07-05
If it is stability you are interested in, then please use Debian (stable). Nothing else comes closer to a near-perfect stable experience. Of course, you might have trouble with hardware support in the current Debian stable release. Maybe it is a good idea to wait till September when the latest Debian stable version (lenny) will be released.

---

### Post by jflaker on 2008-07-05
> **TonyGould said:**
> ...SNIPPED
My question is, what level of stability and reliability should we reasonably expect? My understanding isn't perfect, but I hear for example that ubuntu is based not on the stable debian but on an "unstable" debian release, so if I really wanted rock solid stability I wouldn't use ubuntu, right? 
.....SNIPPED(

Have you tried Vista?  I have and on 2 of the three machines I had a complete meltdown.  I have been using Ubuntu for less than a year, but I can say, the third machine which my wife uses has to be rebooted daily just to maintain usability.  

I can say that Ubuntu outshines Vista any day in stability and especially performance.  Windows Vista is bloated and uses every bit of the 1GB of RAM on the system while Ubuntu uses only 1/3 of the 1GB..........

While under MOST circumstances, Ubuntu will be very stable, it is certain software that may cause lockups....The OS itself is VERY stable.

I will not go back to Windows except at work where I don't have that choice.....but there is rumors floating that my company is going to try a small and isolated pilot of Ubuntu to see if there is feasibility in going 100% open source OS and programs.

---

### Post by ramjet_1953 on 2008-07-05
To improve stability, a few things to consider.

1. Turn of Compiz Fusion. Although this program is now in release, it is still very early days and it can cause problems with lockups.

2. Use only packages in the regular Ubuntu repositories. Do not enable the extra repositories.

3. Do not load kernel updates when they first appear. Wait at least a week and keep an eye on these forums for reaction to new new kernels.

4. On the same note, do not update software packages, just because a new version has been released. What do they say about fixing things that aren't broken?

5. One caveat on the above. You should accept and install security updates.

The above can be simplified into this: Be conservative.

Personally, I only upgrade to a new version every second release and then only after about three months, so that many of the initial bugs have been sorted.

I also only do clean installs, and save my /home directory. Automatic Upgrades to a new version often cause problems, especially if you have installed things not in the standard repositories, or if you have compiled things yourself.

Clean installs are easily achieved if you have an additional hard drive and swap them over for each install. This also allows you to keep the previous install, if things don't work out with the new.

Regards,
Roger :cool:

---

### Post by TonyGould on 2008-07-06
Many thanks guys for all the advice.

Most importantly it sounds like I should generally be cautious, wait 3-6 months after release if I want to avoid more of the bugs. Also, I should look at the forums for a bit of reconnaissance before upgrading, not just for major releases, but also for kernel updates. And finally, be careful about installing loads of extras esp if my system is working.

Tony.

---

### Post by heatblazer on 2008-07-06
> **TonyGould said:**
> Hi,

I'm fairly new to ubuntu, and to linux (although I'm not new to computing). My question is, what level of stability should I expect from an ubuntu release?

I have installed 8.04 on 3 machines (2 laptops and a mythbuntu box), all of which had 7.10 on them previously. Broadly, more hardware is recognised automatically and much more easily than on 7.10, and things are more attractive, but unfortunately on one of the machines I have experienced random hangs with no obvious pattern or error logging in /var/log, which need a manual power off/on (other threads go into this in detail, I don't propose to here). On one of the other machines, wireless support which worked flawlessly in 7.10 once I had compiled up ndiswrapper is now much flakier.

I'm not trying to whine; indeed I'm happy to have moved over to ubuntu and grateful it's there and the community support in particular is excellent. I've just moved my whole desktop at home from Windows to Ubuntu, and it rocks -- I was particularly pleased Thunderbird even shares its data across the dual boot with Windows, but haven't actually felt the need to log back into Windows since transferring my Outlook messages across and setting it up :)

My question is, what level of stability and reliability should we reasonably expect? My understanding isn't perfect, but I hear for example that ubuntu is based not on the stable debian but on an "unstable" debian release, so if I really wanted rock solid stability I wouldn't use ubuntu, right? (I'm not looking for flames here, just asking a question.) Indeed, we don't run ubuntu at work to host our web servers; rather we use Red Hat if I remember rightly, and we sure as heck don't roll out new releases every 6 months. Was I naive to have thought I could use 8.04 as essentially a server to record TV (in hindsight I'd have been better off sticking with 7.10 and upgrading just the mythtv bit).

Also, I think I've fallen into the trap of upgrading to Hardy thinking that LTS means that it's going to be higher quality than 7.10 immediately, but have I made a mistake there? I've seen elswhere that LTS means that it's going to be supported long term, but doesn't necessarily mean that it will be more stable from the get go?

Should I just be going for the .10 releases for example? Or once I have something working, stick with it, because the combinations of hardware and software are just too scary and too time consuming?

All comments welcome, and I hope my question can be taken as the open question that it is.

Tony.


I recommend 7.10 right now. Go for 8.04 LTS at the end of 2008.

---

### Post by TonyGould on 2008-07-06
> **msrinath80 said:**
> If it is stability you are interested in, then please use Debian (stable). Nothing else comes closer to a near-perfect stable experience. Of course, you might have trouble with hardware support in the current Debian stable release. Maybe it is a good idea to wait till September when the latest Debian stable version (etch) will be released.

That's funny, I was thinking I might try Debian eventually when I had some more experience with ubuntu. I'm still on a steep learning curve with ubuntu and I hear that debian is even steeper for someone new to linux.

A few days ago, I tried searching to find out which debian release ubuntu is based on, but didn't have too much success. Is that because I didn't know how to look, or because it picks and chooses from debian? Is hardy largely based on debian etch, even though etch hasn't been released yet?

Tony.

---

### Post by TonyGould on 2008-07-06
> **heatblazer said:**
> I recommend 7.10 right now. Go for 8.04 LTS at the end of 2008.

Thanks, I can only wish I'd had that advice before I upgraded. :) At least I can smile about it.

Tony.

---

### Post by msrinath80 on 2008-07-06
> **TonyGould said:**
> That's funny, I was thinking I might try Debian eventually when I had some more experience with ubuntu. I'm still on a steep learning curve with ubuntu and I hear that debian is even steeper for someone new to linux.

A few days ago, I tried searching to find out which debian release ubuntu is based on, but didn't have too much success. Is that because I didn't know how to look, or because it picks and chooses from debian? Is hardy largely based on debian etch, even though etch hasn't been released yet?

Tony.

It's pretty sketchy these days with Ubuntu versions and corresponding Debian releases. Earlier, Ubuntu versions even featured backward compatibility with Debian (testing branch). But somehow, the Ubuntu folks decided at some point to break binary compatibility with Debian (not on purpose of course) as Debian was getting a little too obsolete for their taste. You could say that Hardy is close to Lenny when it comes to software versions.

---

