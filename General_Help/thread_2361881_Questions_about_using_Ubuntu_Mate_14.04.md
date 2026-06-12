---
title: "Questions about using Ubuntu Mate 14.04"
date: 2017-05-21
forum: General Help
---

### Post by happydog500 on 2017-05-21
As we move foreword to 17, and soon to 18, I have to go back to use 14.04, since the newer ubuntu doesn't work with my hardware (Terminal Commands don't either). 

 Because it didn't work, I had to go back to Mint. I want to use Ubuntu Mate, so the only way is 14.04. 

 In ubuntu 16.04, under Mate Tweeks, it has "Cupertino." This makes it so it's like Apple, with a dock. In 14.04, it doesn't have "Cupertino." I see I can add that to 14, but can I add it without adding a PPA? 

 Another question I have with 14.04 is, I read that they don't maintain it very much (including backports), now that it's "older." This is understandable. I was wondering how much it's not maintained? 

 What exactly does it mean it's not maintained as much? Should it not be used? 

 Thank you,
  Chris.

---

### Post by Bucky Ball on 2017-05-21
Your other option is to post support threads here to deal with the problems you're having with Mate 16.04 LTS. It's what we're here for. :) 

14.04 ain't going to last forever so you're going to need to figure something out eventually. May as well be now. Or are you expecting to by a new computer within the next five years?

All LTS releases are fully maintained for the support life of the release with security updates and updates to the installed software. What is not upgraded are many of the actual apps in an LTS release. Someone else can give you more detail on this, but suffice to say, there is absolutely nothing to worry about as far as Canonical ignoring LTS releases. Far from it.

LTS releases are intended to be rock-solid stable for production machines and to drop the ball with an LTS would be like blowing both feet off with an elephant gun rather than shooting themselves through the foot for Canonical. :)

The interim releases are much more likely to be unstable than an LTS release, but the interim releases have the 'latest and greatest' versions of software installed, probably one of the reasons they can sometimes be less than reliable. Never use them myself, but lots of people are happy with them. 

Another point to remember is that interim releases have nine months support while LTS releases have five years. Unless you need the latest and greatest, which I will remind you does not necessarily mean the 'bestest', then an LTS will save you the hassle of having to upgrade/reinstall your release every six months and should be hassle free computing.

Hope that helps.

(Should an LTS not be used??? In my opinion, that's all I use. I would argue the other way!!! Not really. Canonical don't put they effort they do into the long-term support release for it not to be used. Businesses and anyone that can not afford down time, as well as anyone using their machine for production work who need 24/7 reliability use LTS releases. That's who they're aimed at, among others. LTS is intended to be a rock-solid workhorse that won't break under heavy stress rather than a release that shouldn't be used! I encourage you to use it.)

(PS: Don't bother with 17.04 if you're going there. Support ends in a month or two and then you will be upgrading/reinstalling anyway. Good luck.)

---

### Post by howefield on 2017-05-22
> **happydog500 said:**
> Another question I have with 14.04 is, I read that they don't maintain it very much (including backports), now that it's "older." This is understandable. I was wondering how much it's not maintained? 

Exactly what version of Ubuntu is it that you are asking about ?

If it is any of the Mate 14.04.x versions they are already end of life, at least for the Mate specific packages. Any underlying packages common to Ubuntu will get security fixes and patches till April 2019.

---

### Post by Impavidus on 2017-05-22
Ubuntu Mate 14.04 is no longer supported, as are Xubuntu and Lubuntu, but they all share the same repositories with regular Ubuntu. This means that the software specific to Ubuntu Mate (or Xubuntu, Lubuntu) is no longer supported, but all software it has in common with Ubuntu (or Kubuntu; Kubuntu 14.04 has 5 years of support, although 16.04 only has 3 years) will still get security upgrades. That includes things like the kernel, firefox, most command line tools. So on Ubuntu Mate 14.04, although unsupported, you still get most (but not all) security fixes and it should mostly work.

But it's not guaranteed to work. In principle, it's possible that an update to some software common to both regular Ubuntu and Ubuntu Mate necessitates an update to some software specific to Ubuntu Mate, but the latter will not be made. This caused problems to many with 10.04, when the desktop edition (back then 3 years of support) was no longer supported and was broken by an upgrade to the server edition.

So better find out how to get 16.04 working.

---

### Post by VMC on 2017-05-22
> **happydog500 said:**
> As we move foreword to 17, and soon to 18, I have to go back to use 14.04, since the newer ubuntu doesn't work with my hardware (Terminal Commands don't either). ...
What is your hardware? HD, ram, graphics, etc.

---

### Post by Dennis N on 2017-05-22
Ubuntu MATE 14.04 LTS actually has 5 years support. It is not an official Ubuntu release (it was released in Nov. 2014) and developer Martin Wimpress has pledged to support it for the full 5 yr. duration of 14.04, with the MATE desktop support coming from a Launchpad PPA.

He confirmed all this on the *Linux Unplugged* podcast #66 - available on YouTube.

The first official Ubuntu MATE release was 15.04

---

### Post by happydog500 on 2017-05-23
Thank you all for the reply's. Very, very much. I've been on the forum for a year, nothing works, not even xrandr in Pluma. My hardware, AMD HD 6410D, doesn't work with ubuntu with my set up. Can't get it to boot to DVI-0 primary, VGA-0 Secondary. 

 I love ubuntu and wish I could use it. Thank you for all the help. Sorry we didn't get it to work. I'm going to give openSUSE 42.2 a try. Maybe they have a geek in there forums that can think of something we haven't. 

 Chris.

  Here is the last thread I tried. 

 [https://ubuntuforums.org/showthread.php?t=2361205]("https://ubuntuforums.org/showthread.php?t=2361205")

---

