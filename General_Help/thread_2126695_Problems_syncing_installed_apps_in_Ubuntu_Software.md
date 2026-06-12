---
title: "Problems syncing installed apps in Ubuntu Software Center"
date: 2013-03-17
forum: General Help
---

### Post by Bathroom Humor on 2013-03-17
So, it's that time of year, getting ready to upgrade my Ubuntu to the latest version. As usual I'm jumping in early and the reliability so far is great.

As a key part of my upgrade prep, having my applications sync up in the software center for easy install later on is a godsend.  But as of right now, the syncing feature isn't working out for me.
I open up the sync window in 12.10, and it shows that installations' packages, plus the synced apps from 12.04 (which is no longer installed on my machine, but I guess it sticks around anyway.) But when I log in to my 13.04 installation, it only shows its own applications and no other computer is present. It tells me to sync on the other installation at the bottom, but i've already done this so that isn't a solution. I would like to get this show on the road without having to resort to the less convenient method of making a list and installing them manually.
Also, if there are any alternative methods of getting similar results (creating a automated list of applications that will install easily elsewhere), I'd be happy to see it, too.

Other info: I have two separate partitions with 13.04 and 12.10 on this computer, and i'm doing a fresh install. Not really syncing between different computers, but I don't think it matters to the software center.

Thanks

---

### Post by ibjsb4 on 2013-03-18
There are several ways to backup your installed packages.  I use "Synaptic Package Manager" to backup all installed packages (called a "Markings List").  It can be used when restoring or upgrading to a new version.  Just save full state.

[ATTACH=CONFIG]240307[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager+markings+list&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager+markings+list&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by Bathroom Humor on 2013-03-18
Yea, my next plan was to use Synaptic. But I didn't know if it had something as convenient and simple to work with. But I'll see how well the marking list goes.
Thanks for the input

---

### Post by Bathroom Humor on 2013-03-19
Any other friendly have input into the problem. I suppose I can do with Synaptic (really wish they'd re-include this lovely tool for when the USC doesn't cut it) but it would be much lovelier if a major component of such an important piece of software could be fixed.

I can only speculate that either the servers at Canonical dislike me very much, or the syncing feature doesn't work with development versions for some reason.

---

### Post by Bathroom Humor on 2013-03-19
I guess it's worth pointing out that my main aversion to using Synaptic is that it also grabs a lot of libraries and other packages that I may have used at one time but I no longer need, And I'd like this system to start as clean as it can while having the applications I actually want to use. If Synaptic could differentiate between applications and libraries that would work great but it cannot

---

