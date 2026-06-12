---
title: "[SOLVED] Swiftdove gives Illegal instruction (core dumped) error"
date: 2008-04-30
forum: General Help
---

### Post by tedrogers on 2008-04-30
This is strange.

In 7.10 I had swiftdove 2.0.0.12-2 working fine last week, this was installed through automatix (now defunct). I removed it and installed it again independently of automatix and now it gives me this error when run from a terminal:

```
Illegal instruction (core dumped)
```

If I install 2.0.0.9 instead, it works fine. But then Ubuntu detects an old version, prompts for upgrade to 2.0.0.12-2 and if you install it it breaks the application.

Gawk is installed and up to date.

Removing /home/<me>/.swiftdove and/or removing /usr/local/swiftdove makes no difference. It's proper borked!

I'm using the Pentium M version on an IBM T42 if this matters at all, not that I think it makes a difference, but it might help.

Strange that 2.0.0.9 works and 2.0.0.12-2 doesn't. Swiftweasel (also installed and latest version) runs no problems.

Any ideas anyone?

Thanks.

---

### Post by tedrogers on 2008-05-02
Bump!

Please help me!

---

### Post by tedrogers on 2008-05-04
Bump, bump.

---

### Post by Eric Weir on 2008-05-14
> **tedrogers said:**
> Bump, bump.

I can't help you, Ted, but I'm curious about how Swiftdove works for you. Why did you switch from Thunderbird? I could also use pointers on install Swiftdove.

I've been using Thunderbird for several years now, and the performance has been terrible for me since I started switching over to Ubuntu from Windows. I've downloaded the package for my processor from sourceforge, but I don't know where to go from there.

When I go to unpack it, I'm asked to specify a directory. I have no idea where it should go. [Or do I simply specificy a directory where it should be unpacked and then do the installation from there?]

I noticed that you said when you revert to an earlier version, Ubuntu notices you're out of date and prompts you to upgrade. Is Swiftdove in the repositories? 

Sorry I can't get help, but feedback from a Switdove user would be appreciated. 

Sincerely,

---

### Post by tedrogers on 2008-05-18
Hi,

It seems the problem was just a bug that was particular to my system and swiftdove-pentiumm v2.0.0.12-2 - it was fixed with 2.0.0.14 of swiftdove but they removed the calendar function :(

Thunderbird for me was really slow on XP and Ubuntu....don't know why...but neither are as bad as Evolution which is really really slow to collect mail and process junk. Swiftdove as an optimised email client for specific CPU's is just fast and works damn well IMHO!

Instructions here for adding the repo:

[http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt](http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt)

Hope that helps you. Try it, you'll like it.

---

### Post by Eric Weir on 2008-05-18
> **tedrogers said:**
> It seems the problem was just a bug that was particular to my system and swiftdove-pentiumm v2.0.0.12-2 - it was fixed with 2.0.0.14 of swiftdove but they removed the calendar function :(

Glad to hear the problem was solved. Regarding the Calendar, Sunbird is always an option. In fact, I've gone to it because I don't like the implemention of the calendar in Thunderbird -- or should that be Thunderbird for Ubuntu. It's fine on XP.

>  Thunderbird for me was really slow on XP and Ubuntu....don't know why..You're not alone. A thread I started a few months back continues to get posts from people who're having the same experience,including people with the latest processors and lots of RAM. 

I spent a good part of the day at an 8.04 installfest yesterday, and nobody there could diagnose the problem. [In addition to the difficulties with Thunderbird, there's something going on with my system that makes it clunkier than it should be.] I left feeling pretty discouraged about Ubuntu. I've been spending entirely too much time screwing around with my system. I've learned a lot. But it's cut my productivity at real work -- real for me -- way down.

>  Swiftdove as an optimised email client for specific CPU's is just fast and works damn well IMHO!Glad to hear that. Maybe it'll save Ubuntu for me. I was really ready to go out and by an iMac yesterday. [Still may. They're just such damn beautiful machines, and there are applications that I'm having a difficult time finding equivalents for on Linux.]

>  Instructions here for adding the repo:

[http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt](http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt)

Hope that helps you. Try it, you'll like it.I definitely will, and I hope you're right.

Thanks,

---

### Post by tedrogers on 2008-05-19
Hi Eric,

Everything I said before was related to Gutsy 7.10 - bear with me on this.

Initially I tried Hardy when it first came out (on my IBM T42) and it was giving me errors...although for the first time ever most stuff worked out of the box (wifi, bluetooth etc). The errors seemed not to impact on performance. 

I went back to Gutsy though (I always keep a complete image of my system using Partimage - so easy enough to do) and after a while I got curious again so reinstalled Hardy via upgrade. It still gave me errors, but different ones, so I did a fresh install instead.

Amasing...no errors...evolution mail works like a charm and it's faster than swiftdove ever was! For now at least, I'm sticking with Evolution mail...and as a native ubuntu app it interconnects with other apps like tomboy notes (which I use a lot).

Don't go the mac route if you can resist....yes they're sweet and I use one at work...but its locked down and you can't fiddle as much. I know you like to fiddle really don't you! :)  And anyway, darwin isn't as nice as bash. For me Hardy is the sweetest ubuntu yet....despite early teething problems that have been resolved in the software development.

---

### Post by Eric Weir on 2008-05-19
> **tedrogers said:**
> . . . . after a while I got curious again so reinstalled Hardy via upgrade. It still gave me errors, but different ones, so I did a fresh install instead.

Amasing...no errors...evolution mail works like a charm and it's faster than swiftdove ever was! For now at least, I'm sticking with Evolution mail...and as a native ubuntu app it interconnects with other apps like tomboy notes (which I use a lot).
Thanks for the update, Ted. I'll have to give Evolution another try. My main objection in the past was the way it handled filter creation. I think in my brief fling with it after installing Hardy that seemed to have been improved. I do love the Thunderbird extensions. But I'll give Evolution a try -- when I get time; right now -- well, not *right* now -- I'm focused on meeting a writing deadline.

> Don't go the mac route if you can resist....yes they're sweet and I use one at work...but its locked down and you can't fiddle as much. I know you like to fiddle really don't you! :) Well, I've been very tempted lately. I've been wondering whether I wasn't jinxed for Ubuntu. Not even confident that things would be better if I went out and got a good new machine to put it on. [There's a guy here who puts together machines with Ubuntu installed.] 

I do find the whole open source idea very, very appealing. Might be steppin' on your toes politically here, but I love it when community beats capitalism at it's own game. [But then Mark Shuttlesworth doesn't exactly have clean hands in that regard, not that he's ever done anything devious or dishonest, and his heart certainly seems to be in the right place as far as Ubuntu is concerned.] And the though of shelling out $1500 or so for a Mac is a deterrant. so I think I'm safe for a while. 
> For me Hardy is the sweetest ubuntu yet....despite early teething problems....That's encouraging. I think I might give in here soon and just go to straight Ubuntu. I never really gave it a chance first time around. Skipped on to Kubuntu and stayed there several months. And made my fresh install after Hardy came out Xubuntu.

I do love the graphic of the heron.

Regards,

---

### Post by tedrogers on 2008-05-21
Well, you don't have to stick with Ubuntu....Fedora 8 (or is it 9 now) is a sweet ditro too.

It actaully detects my hardware better as well, ATI etc (probably because its less "bleeding-edge") but it works well out of the box.

Almost all of what you can get in Ubuntu you can get in Fedora.

My only gripe is that the password nags are more frequent.

Evolution is a proper bugger for mail filtering...I remember now why I liked Thunderbird again! :) LOL

---

