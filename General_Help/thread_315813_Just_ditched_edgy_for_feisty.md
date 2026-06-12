---
title: "Just ditched edgy for feisty"
date: 2006-12-09
forum: General Help
---

### Post by wgscott on 2006-12-09
I was about to regress to 6.06 due to what has become an intractable problem -- some of my drives become read-only, system freezes, etc.

I decided before I did that to upgrade to feisty, just in case that fixed the problem.  It is too early to tell if my problem went away, but the upgrade was surprisingly smooth, given the development status of feisty (I had nothing to lose except my data :p ).  I had to reboot once in the middle to get out of apt-get purgatory, but apart from that it seemed to go well.

So far.

One annoyance, which is probably a feature, is the desktop seems to have twice as much area as the display, so when you move the mouse it reveals hidden regions of the desktop.  I can see why this could be handy but I'd like to turn it off.  Anyone know how?  It seems to do this in at least Xfce4 and KDE.

---

### Post by PriceChild on 2006-12-09
[SIZE=5][COLOR=Red]**I strongly advise you ditch Feisty... You're about to experience MAJOR breakage.**[/COLOR][/SIZE]
> **wgscott said:**
> One annoyance, which is probably a feature, is the desktop seems to have twice as much area as the display, so when you move the mouse it reveals hidden regions of the desktop.  I can see why this could be handy but I'd like to turn it off.  Anyone know how?  It seems to do this in at least Xfce4 and KDE.Welcome to your first bug.... get out while you still can.

---

### Post by crimsun on 2006-12-09
> **wgscott said:**
> One annoyance, which is probably a feature, is the desktop seems to have twice as much area as the display, so when you move the mouse it reveals hidden regions of the desktop.  I can see why this could be handy but I'd like to turn it off.  Anyone know how?  It seems to do this in at least Xfce4 and KDE.

Check whether ``xdpyinfo|grep dimensions'' corresponds to the Modes defined in /etc/X11/xorg.conf.

---

### Post by max.diems on 2006-12-09
PC, I would have said you were exaggerating, but you're not. Why is it that you don't have to be a developer to use testing versions, at least until around a month before release?

---

### Post by PriceChild on 2006-12-09
> **max.diems said:**
> PC, I would have said you were exaggerating, but you're not. Why is it that you don't have to be a developer to use testing versions, at least until around a month before release?You don't... I'm not a developer. But by the sounds of it he's going to be using this as his main OS on this PC... it won't be at all stable and will die very VERY soon.

He should go right back to Dapper or figure out what's wrong with edgy.

---

### Post by kinematic on 2006-12-09
> **PriceChild said:**
> [SIZE=5][COLOR=Red]**I strongly advise you ditch Feisty... You're about to experience MAJOR breakage.**[/COLOR][/SIZE]

if no one was to use feisty then how would the devs be able to squat bugs ;)

---

### Post by PriceChild on 2006-12-09
> **kinematic said:**
> if no one was to use feisty then how would the devs be able to squat bugs ;)See below
> **PriceChild said:**
> You don't... I'm not a developer. But by the sounds of it he's going to be using this as his main OS on this PC... it won't be at all stable and will die very VERY soon.

He should go right back to Dapper or figure out what's wrong with edgy.

---

### Post by wgscott on 2006-12-09
Unless it starts to eat my data and crawls over the internet to consume my remote backups, sleeps with my wife, poisons my dog with 210Po, casts 200,000,000 more votes for George Bush, and starts a nuclear war with France, I don't have a lot to lose at this point. If it is unstable, I am quite happy to throw it in the trash (zero the partition and install 6.06).

:-D 

I use this mainly as a unix machine.  If it keeps the disks mounted in rw mode, it is doing better than the supposedly viable Edgy as far as I am concerned.

---

### Post by wgscott on 2006-12-09
> **crimsun said:**
> Check whether ``xdpyinfo|grep dimensions'' corresponds to the Modes defined in /etc/X11/xorg.conf.

Yeah, it is bigger than the native display, and does not match up with any of the non-default options either.

---

### Post by wgscott on 2006-12-09
> **PriceChild said:**
> See below


Having my slave drivers spontaneously become read-only is a cockroach of a bug, and rendered the machine useless.  I wasted a week of my life trying to track it down, and I can either reinstall 6.06, or upgrade to feisty, find that the bug remains or new intractable bugs exist, and then reinstall.  One step forward, two steps back.  If you can warn me of a specific problem, I guess I would be more likely to ditch it.

---

### Post by wgscott on 2006-12-09
> **crimsun said:**
> Check whether ``xdpyinfo|grep dimensions'' corresponds to the Modes defined in /etc/X11/xorg.conf.

Thanks.  I manually edited xorg.conf and updated the md5sum and all is working normally now.

Apart from the fact that the world is about to come to an end. :-D

---

### Post by iamhugeinjapan on 2006-12-10
Read the Feisty development forum and look back at the early days of the Edgy development forum etc. Early testing is a world of pain. If things are working for you right now and you are determined to stay with Feisty, then do not update anything for a long time.

You wont be happy when you turn on your pc to check your email quickly and find you have no xserver at all.

---

### Post by kerry_s on 2006-12-10
If it's running okay now, just don't update or at least wait & check the forums for any problems. I'll usually wait a week before upgrading & only if i don't see any one having problems with updates. The only problem i've had is with the feisty kernel, for some reason it won't boot for me, it just stops after loading the usb, so i'm still using the edgy kernel which works very good.

---

### Post by PriceChild on 2006-12-10
Good luck to you.

---

### Post by wgscott on 2006-12-10
Unfortunately, I still have the same bug that made Edgy unusable -- the slave drive file systems are read-only. So even though nothing new bad has happened to me with feisty, I won't be using it.

So I will zero the root partition and install 6.06, which was the last time things behaved for me in terms of disk arbitration.  I think it is time for a clean install.

The other possibility, of course, is that I have a hardware problem that coincidently appeared with the Edgy release.

Anyway, my short life with Feisty did not reveal any (new) problems.  I don't use most of the desktop stuff on this machine, so I haven't given it a real test, but NFS, smb mounts, compilers and so on seem to be fine (and are probably unchanged from 6.06 or 6.10).

Anyway, thanks.

I thought it was worth a shot to try a new kernel version before I gave up on having an up to date Ubuntu.  It is rather frustrating that 6.10 rendered my computer unusable.

When I first started with Ubuntu, I ditched Red Hat, and I was amazed how everything "just worked", kind of like what I am used to with OS X.  Then each new update had at least one glitch that would have been a show-stopper if I was not enough of a unix geek to hack it into shape.  I worry maybe that Ubuntu is moving too fast. 6.06 is supposed to be a long-term release, so I was suprized how buggy it was.  6.10 seemed to fix the most annoying of these, and would have been a welcome upgrade, except for the nightmare I am having with the slave drives becoming read-only.

I'm on the verge of looking now for a new linux distribution that I can count on to simply be stable.  I use OS X for most of my computer needs, but I need to have a linux PC to run -- get this -- some proprietary software.  I thought I had found the perfect Linux distribution with Ubuntu, and except for this latest bug (which could be a hardware problem for all I know) it pretty much has been.

Anyway, thanks for the advice.  I thought Feisty would at least be worth a try before I gave up.  One thing I did like was the new version of the nvidia driver.  (Since the main point of this machine is to run restricted software, I don't have the sense that I am compromising.)

---

### Post by PriceChild on 2006-12-10
Maybe you should file bugs instead of trying to hack it when things regress?

---

### Post by wgscott on 2006-12-10
> **PriceChild said:**
> Maybe you should file bugs instead of trying to hack it when things regress?

I have (except for the most current bug, which is 10 orders of magnitude worse than anything previously, which qualify more as annoyances or possibly user error).

Sorry, I didn't mean to make light of your warning. It is just that by "upgrading" to feisty I had nothing to lose unless it destroyed my data (all of which is backed up anyway).

 I've been doing upgrades instead of clean installs for the last ca. 4 releases, so it is possible I have an old configuration file that is messing stuff up with disk arbitration.  It is a hard problem to reproduce, as it has a random element, and I've chased down a lot of false leads.  A good bug report needs to tell a developer how to reproduce the problem.

---

