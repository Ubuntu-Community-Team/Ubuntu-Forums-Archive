---
title: "Change from cinnamon-nightly to cinnamon-stable?"
date: 2013-09-30
forum: General Help
---

### Post by josephellengar2 on 2013-09-30
I am trying to shift from the nightly to the stable cinnamon builds (Ubuntu 13.10) and am having a lot of trouble doing so-- every time I do I get package conflicts.

So my first through was to do a ppa-purge, remove all of the nightly packages, and then just add stable in. This didn't work and I got terrible unresolvable conflicts that were only cleaned up when I re-added nightly.

I also tried manually removing all of the nightly packages. Same deal.

I also tried doing it all from command line with X not on and through a different DE.

I also tried removing all X-related packages (gnome, cinnamon, even my qt packages) or doing it through various package managers (Synaptic, apt, software center, etc).

Is there any "correct" way to do this? I thought ppapurge was the correct way, but it just didn't work. Any advice would be awesome. Thanks!

---

### Post by CaptainMark on 2013-09-30
Well as with any unstable branch especially automated nightly builds they are not packaged with removal in mind, there's obviously a package which has been updated and apt-get is unable to figure out how to downgrade it. Remove the nightly ppa and then you can try removing all packages listed in the cinnamon nightly ppa here [https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly?field.series_filter=saucy](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly?field.series_filter=saucy) until you have completely removed all traces of the nightly build then remove any conflicting packages and then finally try adding the stable ppa, I don't much fancy your chances of getting it to work correctly but if that's the case just chalk it up to experience and move on with a fresh install

---

### Post by josephellengar2 on 2013-09-30
> **CaptainMark said:**
> Well as with any unstable branch especially automated nightly builds they are not packaged with removal in mind, there's obviously a package which has been updated and apt-get is unable to figure out how to downgrade it. Remove the nightly ppa and then you can try removing all packages listed in the cinnamon nightly ppa here [https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly?field.series_filter=saucy](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly?field.series_filter=saucy) until you have completely removed all traces of the nightly build then remove any conflicting packages and then finally try adding the stable ppa, I don't much fancy your chances of getting it to work correctly but if that's the case just chalk it up to experience and move on with a fresh install

Unfortunately I have already done that, removing and purging packages one at a time. I thought that if I removed everything it might work, but not so. And ppa-purge gives me an error "could not find package list". Any other ideas? Or any ideas how I could repair ppa-purge?

---

### Post by josephellengar2 on 2013-10-07
bump. Any other suggestions?

---

### Post by josephellengar2 on 2013-10-12
One more try. Bump.

---

