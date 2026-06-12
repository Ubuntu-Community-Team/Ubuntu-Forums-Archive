---
title: "A couple questions about packages in the repositories"
date: 2008-04-25
forum: General Help
---

### Post by shaggy999 on 2008-04-25
I have a couple of questions that have come up for me after installing Hardy Heron:

1) There are two packages for adblock called *mozilla-firefox-adblock* and *adblock-plus*. Are these the same packages? Is one for firefox2 and one for firefox3? Is one a dummy package referencing the other? This isn't clear to me.

2) Where is VMWare? I enabled all the repositories, including partner, and I can't find it anywhere.

3) I keep reading about how Canonical will only be releasing updates to packages now. Does that mean that throughout the lifetime of hardy there will be no new programs added to universe, multi-verse or the other repositories? Meaning if some new cool program comes out in 3 months and there's a debian package for it there won't be a package in the repositories until the Ibex release (if Canonical decides to support it)?

4) I want to set up an apt-mirror locally but the primary server that I normally use is obviously being hammered right now. I switched my computer to download from a different mirror but I'm wondering if I set up apt-mirror to mirror one of the mirror servers can I later change the mirror cache to be reflecting the primary ubuntu package repositories without it deleting everything and starting over?

Thanks for any help!

---

### Post by SunnyRabbiera on 2008-04-25
for adblock I am unsure

VMware is not really open source so its not in the repositories, if you need a good VM software try virtualbox, I find it pretty decent.

for your third question if there is any new software I am sure it will be ported on to hardy at some time, either by the official repos or third parties.

for your fourth, just hang out for a couple of days and things might get better.

---

### Post by shaggy999 on 2008-04-25
I tried installing virtual box and it failed. Plus, I already have several vmware images that I had set up and was using in gutsy.

I know vmware isn't open-source, but it's always been available in one of the repos.

---

### Post by fluteflute on 2008-04-27
In Fiesty and Gutsy the mozilla-firefox-adblock package is the adblock extension.

As adblock is no longer developed (and adblock plus is), from Hardy the mozilla-firefox-adblock package is simply a dummy package which installs the new package adblock-plus. This ensures upgrades from Gutsy to Hardy automatically install the new adblock plus and there is also a descriptive file name.

---

### Post by Ioky on 2008-04-27
> **shaggy999 said:**
> I tried installing virtual box and it failed. Plus, I already have several vmware images that I had set up and was using in gutsy.

I know vmware isn't open-source, but it's always been available in one of the repos.

Well, I don't think so, what you might talking about is Vmware player. They are difference. you will always need to install VMware on your own, just go to there site and download it. It is pretty easy. 

And yeah, there will be new software ported to HH. Beside, you can always do it yourself, Install it manually.

---

### Post by shaggy999 on 2008-05-06
Thanks for the replies. I just wanted to post back and let everyone know that I was able to successfully rename the folder of my Ubuntu mirror to the primary repository server's at canonical and changed the appropriate links in the mirrors.list file and it synced up perfectly without having to re-download the entire repositories.

---

