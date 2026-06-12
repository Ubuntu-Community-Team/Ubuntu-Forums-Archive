---
title: "Firefox Very Glitchy and slow"
date: 2016-10-29
forum: General Help
---

### Post by simon114 on 2016-10-29
Hi community,

I have just done a fresh install of Ubuntu 16.04 I have 

4GB of PC1600 ram 
SSD 250GB 
AMD A4 CPU


Firefox Is very glitchy and scrolls badly, become unresponsive and generally behaves badly. I did uninstall and reinstall but all continues to behave badly.

Are there any settings I can change to improve performance...if not any other browser with flash support that I could change to? (as a last option)

Thanks, If you need some system info please tell me the terminal commands and I will repost back the results.

Thank-you.

---

### Post by ajgreeny on 2016-10-29
See if everything works properly if you start FF with a new profile using command firefox -p in terminal, -> "Create new profile".

This sort of problem is often related to a corrupt or problem profile; maybe an update to one of your add-ons has caused this.  You can also restart FF without any add-ons from the Help menu to see if that solves it for you.

---

### Post by simon114 on 2016-10-30
> **ajgreeny said:**
> See if everything works properly if you start FF with a new profile using command firefox -p in terminal, -> "Create new profile".

This sort of problem is often related to a corrupt or problem profile; maybe an update to one of your add-ons has caused this.  You can also restart FF without any add-ons from the Help menu to see if that solves it for you.


Good morning ajgreeny,

I have tried that as you instructed, but the result is the same. It really looks to me like some sort of cache/memory  problem in firefox, like it need more ram to work but not getting it..when firefox is running, i have 1.1 GB of spare ram, so I know that there is ram available. and the firefox and ubuntu are vanilla fresh(out of the box) installs with no addons/plugins  installed

---

### Post by blitzen11 on 2016-10-30
This is happening to me aswell. I ditched Firefox to Chrome and works well. I have 8Gb of ram and a quad-core CPU, still lags. :/

---

### Post by Bill Roberts on 2016-10-30
Same here.  I had assumed it was my internet connection, but after an extended period of monitoring, I realized it was only Firefox.  Other web connected software such as games weren't affected. Switching to Chromium seems to be the best answer for now. As a Firefox user since the beginning, this is a great disappointment and I'm not convinced telling Mozilla about it will actually help.

---

### Post by &amp;KyT$0P# on 2016-10-30
Have you tried ajgreeny's suggestion on the [official Mozilla build]("https://www.mozilla.org/firefox/all/") of Firefox?

---

### Post by Bill Roberts on 2016-10-30
No, I have not and I do not intend too. The same problem was happening on two different ubuntu machines, used by two different users with different profiles. I don't see the point, especially in light of the replies by simon114 and blitzen11.

---

### Post by &amp;KyT$0P# on 2016-10-30
> **Bill Roberts said:**
> The same problem was happening on two different ubuntu machines, used by two different users with different profiles. 
These different ubuntu machines wouldn't all happen to have the "stock" package manager version of Firefox, would they?

> I don't see the point, especially in light of the replies by simon114 and blitzen11.
The point is to check if this issue is specific to the Ubuntu distribution build of Firefox.

I've had some of the weirdest issues on distros' builds of Firefox.  Ran through standard troubleshooting until my wits end.  Eventually, as a last resort, I put in the official Mozilla build, thinking '*Eh, doubt this'll do anything, but whatever*', and bam, issue gone.  Odd, indeed, but true all the same.

---

### Post by Bill Roberts on 2016-10-30
I decided to try it, and found this page [http://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](http://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds) helpful. At a couple of points I got some really disturbing error messages and a required reboot (how the image got involved escapes me) but I'm currently running an "official Mozilla copy of Firefox". I'll try and remember to keep you posted on my progress. My preliminary evaluation is positive, but that leaves me with a disturbing sense of distrust of the distro. :-)

---

### Post by vasa1 on 2016-10-30
> **Bill Roberts said:**
> ... that leaves me with a disturbing sense of distrust of the distro. :-)
Maybe you'll find something more trustworthy over at Distrowatch. All the best :-)

---

### Post by &amp;KyT$0P# on 2016-10-30
> **vasa1 said:**
> Maybe you'll find something more trustworthy over at Distrowatch. 
That's kind of doubtful.  Firefox packages are like this on just about every Linux distro as far as I can tell.  Let's just say, around where I hang out, Ubuntu is not the most notable distro for Firefox problems.

Something like 99% of all software you'll use from the repositories will work flawlessly for you.  Why reach for the inhalers over the remaining 1%?  Just use a PPA or official download and enjoy your Ubuntu again.

Cheers. :)

---

### Post by vasa1 on 2016-10-30
> **halogen2 said:**
> That's kind of doubtful. ...

Hmm, maybe I took the words literally.

Anyway, distrust of the distro apart, this thread seems to be going the way many browser threads usually go ;)

There may be more "me too posts" and advocates of Seamonkey, Midori, Epiphany, Slimboat/jet(?), PaleMoon, Qupzilla, etc may pitch in as well.

OP, you could open *about:preferences*, click on the *Advanced* tag and see what's checked there. I have an oldish laptop, no GPU, and so I keep *autoscrolling*, *smooth scrolling*, and *hardware acceleration* off (=unticked).

---

### Post by ajgreeny on 2016-10-31
Another thought on this; try uninstalling the **xul-ext-ubufox** extension which is the **ubuntu modifications for firefox** package, installed by default but certainly not needed, and something which I have always removed completely, though you could  disable it in the Tools-> Add-ons ->Extensions page of FF if it worries you to remove it.

---

### Post by elim-qiu on 2016-11-08
I uninstalled Firefox, not just for the performance: it has problems rendering MathJax contents!

I'm using Midori, QupZilla and Opera instead.

---

