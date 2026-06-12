---
title: "Should I upgrade Dapper to Gutsy?"
date: 2007-10-25
forum: General Help
---

### Post by DanielC on 2007-10-25
I currently run Dapper Drake LTS and I'm happy with it. I'm trying to answer two questions:

- Should I upgrade to Gutsy?
- If so, what's the best way to do so.

About my computer:
* This is a desktop. No weird hardware, on-board video, sound and ethernet. I don't discount hardware problems, but they are not too likely.
* CPU: Celeron 2.66GHz ;  RAM: 1.5 GB DDR ; HD: 12 GB free disk space.
* Work computer. I can accept downtime on Saturday but it must be up working.

About me:
I did not upgrade to Feisty and Edgy before because I figured they were less stable. The support period for Gusty ends at about the same time as Dapper (mid-2009) so I figure that Gusty is more stable so I feel better about upgrading.

I am an experienced user, I've been Linux-only since before Gnome. But that doesn't mean I enjoy admin tasks, I hate admin tasks. What I love about Ubuntu is that it "just works" and it stays out of my way.

Other:
I'd love to see what's new and exciting in Gusty. And I figure that eventually I'll need to upgrade anyways, so Gusty is a good opportunity.

I'm concerned about going through Edgy and Feisty on my way to Gusty. But I don't imagine that straight upgrades from Dapper to Gusty are supported. Are they?

Any advice would be much appreciated.

---

### Post by rykel on 2007-10-25
I upgraded from Dapper to Edgy, Feisty and Gutsy over 2 days... and at this point of time, I would suggest that NO, you do not upgrade to Gutsy yet...

It seems like quite a few of us are experiencing severe lockups of our system while using the OS.

However, the Gutsy artwork, look-and-feel etc. definitely surpasses Dapper.

---

### Post by Craigus on 2007-10-25
If this is a mission critical computer I'd strongly suggest clean installing on a separate partition to try Gutsy. Leave your working Dapper installation as is.

---

### Post by timcredible on 2007-10-25
I've installed gutsy on 2 machines so far, no problems at all on either.  i always do a clean install though.  if there's new versions of software you want, install gutsy.  if you don't have any interest in new versions, keep dapper.

---

### Post by jespdj on 2007-10-25
Just download a Gutsy ISO image, burn it on a CD and boot from it, and see if you have any problems running it live from the CD.

If the computer is critical for your work and you can't afford to have it offline for more than two days, then I'd say, don't take the risk unless you have a really good reason to do it.

---

### Post by Zill on 2007-10-25
DanielC: I am in a similar situation to you - I value the long term support of Dapper as I need reliable systems.  In my view, all the versions since then have not really been stable enough to trust for "real" work.  Great for experimenters but not for me!

I will wait for the next long term support version, [Hardy Heron (v8.04 LTS)]("https://wiki.ubuntu.com/HardyHeron"), which is due out next April.

I would guess that when this is released, the Ubuntu Update Notifier will advise this and then give us the option of upgrading automatically.  Hopefully this should then be a fairly painless process :confused:

---

### Post by mali2297 on 2007-10-25
For me, Gutsy is less stable than Feisty. As I have a laptop, the main issue is *Suspend to RAM* which worked fine in Feisty but freezes the system in Gutsy. (Just my personal experience.)

I would suggest that you wait for Hardy, the next LTS release which will come in April 2008.

---

### Post by mojoman on 2007-10-25
> **mali2297 said:**
> For me, Gutsy is less stable than Feisty. As I have a laptop, the main issue is *Suspend to RAM* which worked fine in Feisty but freezes the system in Gutsy. (Just my personal experience.)

I would suggest that you wait for Hardy, the next LTS release which will come in April 2008.

I'm still on Feisty but I miss Dapper a bit. Never even tried Edgy and from the things I've read about it I'd say that was far from stable. I'll probably stick with Feisty until Hardy comes out and then do a clean install. I like the LTS idea but I've been using Debian Lenny more and more lately. Very long-term and very stable though it requires a little morefrom the user (but not that much nowadays).

---

### Post by Em-Buntu on 2007-10-25
I'd strongly suggest you upgrade to Feisty and wait for the numerous bugs to be resolved in Gutsy before upgrading.
I've been running Feisty for awhile and had it running so well until I made the mistake of upgrading to Gutsy. Now the system seems to run two time slower and Mozilla hangs on every other website. 
Too many problems with this release. It seems to still be in the beta stage.

Stay with Feisty Fawn for now.

---

### Post by rykel on 2007-10-25
Pals,

I have narrowed down my Gutsy freezes to (possibly) Bittorrent... can any of you try running some downloads in Azureus and see if it freezes up your PC/laptop?

Thanks!!

---

### Post by Maestro23 on 2007-10-25
> **rykel said:**
> Pals,

I have narrowed down my Gutsy freezes to (possibly) Bittorrent... can any of you try running some downloads in Azureus and see if it freezes up your PC/laptop?

Thanks!!

Azureus freezes many system I can see from reading the forums.  I use ktorrent and deluge with no freezing problems.  And this is with compiz-fusion running also.

---

### Post by DanielC on 2007-10-25
Thanks for all the help guys. It's been immensely useful. I see that Gusty is not quite as stable as I had imagined. So I will definitely not upgrade Dapper. But I like Craigus' idea of putting Gutsy in a separate partition to try out. I especially like it because I don't have to go through intermediate distributions. I could even go from Dapper to Hasty without going through Edgy, Feisty and Gutsy.

One problem is that I only one have one big partition. Could someone confirm that [[COLOR="Navy"]**GParted**[/COLOR]]("http://gparted.sourceforge.net") can resize a partition** without destroying the data in it**? I'd think that this would be obvious, if it destroyed the data I wouldn't call it "resizing" in the documentation but I thought I'd ask anyways.

The Ubuntu LiveCD comes with GParted, right? So I can test the LiveCD first like jespdj said and if I like it I'll fire up GParted.

Thanks again.

---

### Post by mivo on 2007-10-25
Since you are happy and satisfied with your system, I would stick with Dapper until the next LTS release in April. My experience with the Gnome-version of Gutsy has not been flawless and I went back to Feisty on my production desktop. (Xubuntu Gutsy however works well on a different computer.) Unless there are features in Gutsy that you need or really want, waiting for Hardy is probably best.

Edit: GParted can resize partitions without data loss, but it is never risk-free, so while it is likely to work, there is a small chance that something goes wrong and data is lost. A backup is highly recommended.

---

### Post by monoufo on 2007-10-25
I have no problem with Azurues.  I may be using a different version than you though.  I found a proposed version on launchpad a while back that fixed a bug with java and have been using it ever since.  

I do have problems with flash and javascript. Also, the computer won't hibernate on its own.  more recently open office has been crashing too.  I'm hoping a fresh install will fix these issues.  the computer hasn't been fresh installed since Gutsy tribe 5.

---

### Post by rykel on 2007-10-25
> **monoufo said:**
> I have no problem with Azurues.  I may be using a different version than you though.  I found a proposed version on launchpad a while back that fixed a bug with java and have been using it ever since.  

I do have problems with flash and javascript. Also, the computer won't hibernate on its own.  more recently open office has been crashing too.  I'm hoping a fresh install will fix these issues.  the computer hasn't been fresh installed since Gutsy tribe 5.

Wow, it sounds like your problems will open up another can of Gutsy worms!!   :lolflag:

---

### Post by Neostar on 2007-10-25
I think the real problem is the new kernel, it's causing a lot of problems on a number of other distributions :(

---

### Post by justinflavin on 2007-11-06
If your box is mission critical for your work , I'd wait for Hardy Heron - the next release , as it will be an LTS release , as Dapper was.

"Hardy Heron will be a LTS (Long Term Support) release and will be supported with security updates for five years on the server and three years on the desktop."

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Heron is due out in April 2008.

---

### Post by justinflavin on 2007-11-06
> **Neostar said:**
> I think the real problem is the new kernel, it's causing a lot of problems on a number of other distributions :(

yeah - i'm seeing that on some laptops - they work just fine on Feisty, but won't even boot off the Gutsy CD. i get a hard lock during the Ubuntu splash screen.

not good.

---

