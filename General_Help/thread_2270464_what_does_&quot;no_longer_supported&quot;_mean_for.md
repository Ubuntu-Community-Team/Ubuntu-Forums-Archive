---
title: "what does &quot;no longer supported&quot; mean for Ubuntu?"
date: 2015-03-23
forum: General Help
---

### Post by pellicle on 2015-03-23
Hi

I presently use XP as my main OS (well and win7 at work) and am considering moving over to Ubuntu to allow me to leaverage older machines which still work (and means I perhaps don't have to spend buck on laptops / hardware at the moment).

I've put 11.04 on my X31 and it seems to run nicely (no flickering which I got with an other distro) but whenever I try to install things I get "check internet connection" messages.

reading the details I see that the url the Ubuntu Software Center is attempting to access is:

 [http://au.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources)

which is apparently closed ... does this mean that I simply can't get software for this distro anymore? Surely I should still be able to access what was already available?

no?

So does "unsupported" mean I can't even get stuff which was developed?

Thanks

---

### Post by howefield on 2015-03-23
It essentially means no more security updates for that version.

You can still get the software that was in 11.04 repository by pointing to the old.releases repositories, would I recommend it? .. no.

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Lars Noodén on 2015-03-23
I would second Howefield's recommendation to avoid end-of-life versions.  

If you're looking to spark new life into very old machines, then you might look at derivatives like14.04 LTS  Xubuntu or Lubuntu instead which use fewer resources for the GUI itself.  There are even lighter options if you are willing to go a la carte and choose a Window Manger instead of a Desktop Environment.  Even lighter would be Puppy Linux.  What processor and RAM do you have on the X31?

---

### Post by Holger_Gehrke on 2015-03-23
It also means you'll be on you own when you run into problems, since most everybody has moved on from that version. 
I've been in a similar situation myself recently, having gotten an old notebook from 2004 (or thereabouts, P4 with 1G of RAM and an ati mobility 9000) and now it's running so well with Lubuntu 14.04 that I'm seriously considering switching my newer main machine that's still running Ubuntu 12.04 to that.

---

### Post by grahammechanical on 2015-03-23
We get a new release of Ubuntu every six months, at the end of the 4th and 10th months.  It is how Ubuntu keeps up to date with improvements made to the Linux kernel and the other open source components used in Ubuntu. Every two years we get a release that is termed LTS (Long Term Support) which is supported for 5 years. What this means is the LTS version will get an upgrade every 6 months or so until a few months after the next LTS version has been released and then security fixes for the rest of the support period. The 6 monthly releases in between the LTS releases are only supported for 9 months. That is enough time to upgrade to the next 6 monthly release.

Each version of Ubuntu has its own software archives or repositories. Once a version has reached "end of life" those repositories are closed. The archives are still around but they have been moved to another location. This is why you are getting those connection errors. The URLs to the repositories are no longer accurate.

So, with Ubuntu we have the option to use an LTS release and upgrade to the next LTS release or the LTS release after that. So, if we install Ubuntu 12.04 we should either be upgrading to 14.04 or intending to upgrade to 16.04 before Ubuntu 12.04 reaches end of life.

Or, the option to install one of these interim releases with 9 months support and upgrade to each new release within 3 months of its being released.

Considering we get all this without paying anything, I think we get a good deal. Ubuntu 11.04 is running nicely, you say but until we know the hardware specifications, including the graphic adapter there is a possiblity that Ubuntu 12.04 or later may not run as nicely. This is why others are recommending Lubuntu.

Regards.

---

### Post by ajgreeny on 2015-03-23
I am like Holger in so far as I have a fast new computer, but I see no point in running a system with a GUI that I don't like just because I can.  As you will see from my signature I run Xubuntu 14.04.2, in my view the most classic, modern and configurable DE now available.

Of course, you may disagree and love unity: that's the beauty of Linux; you can use whatever DE you want on top of the underlying OS so that it works for you as you want.

---

### Post by Vladlenin5000 on 2015-03-23
> **ajgreeny said:**
> (...) I run Xubuntu 14.04.2, in my view the most classic, modern and configurable DE now available.

Is it a classic modern or a modern classic? :lolflag:


PS - I certainly disagree and love Unity. And that's the beauty, indeed.

---

### Post by ajgreeny on 2015-03-23
> **Vladlenin5000 said:**
> Is it a classic modern or a modern classic? :lolflag:


PS - I certainly disagree and love Unity. And that's the beauty, indeed.
Well, you make your own mind up about that.

Ah, I see you already have.
There you are then; point made!

---

### Post by pellicle on 2015-03-24
Thankyou everyone for your contributions.

I've been a long time Win user but in my job develop mainly on Unix systems. I'm not fond of unix administration (we have a team for that) but like the environment. I'm not liking where Win is going and so I'm looking to move to a platform which I can sweep my stuff along with me (I still have heaps of legacy stuff on my Win2K box which I use {such as Nikon scanners}), so having a platform where I can put on a virtualisation for those legacy tools and still move forward (with browsers and whatnot) it would be good.

I have used redhat back some time ago but back then there were problems with wireless and peripheral support.

My first experience with Ubuntu was with version 9 which I liked. I was pleased to find that 11 installed on my X31 but will try the lubuntu this weekend to see if I can get to 14 there.

Next on the list will be experimenting with virtualisation and seeing if my win2K will run in there (and maybe my XP too)...

---

