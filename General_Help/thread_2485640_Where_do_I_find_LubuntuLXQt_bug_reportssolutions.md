---
title: "Where do I find Lubuntu/LXQt bug reports/solutions?"
date: 2023-04-04
forum: General Help
---

### Post by ne29914 on 2023-04-04
I've completely lost my way and getting lost in GitHub, GitLab, Launchpad etc. (I may be missing some other location), and it's unclear which one is the "official" one. lubuntu.me is no help.
Can someone point me in the right direction, please?

---

### Post by guiverc on 2023-04-04
**Lubuntu** uses launchpad for bug reports.

I'll provide our wiki page on bug reports, being [https://phab.lubuntu.me/w/bugs/](https://phab.lubuntu.me/w/bugs/)

( *You'll note it still contains the LXDE -> LXQt package differences, I've been very reluctant to remove that*, *particularly as I find many users still refer to app/package names using the older LXDE app names, even though they're now using modern LXQt*;* okay I like history too! * )

If I find a bug, I report it first on launchpad..  

eg.  I found *floppy** drives* with *a floppy inserted* mucked up Lubuntu installs, so I reported it on launchpad, the site where Ubuntu & Lubuntu track all issues, being [https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1873128](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1873128)

I then QA-test the issue with the *latest* version available; which means the *development* release (currently *lunar*). Then I file upstream (*this is where I find it can get confusing... where is upstream for that specific package is package specific*).

My upstream report can be found here - [https://github.com/calamares/calamares/issues/1393](https://github.com/calamares/calamares/issues/1393) (*being correct for calamares*).

For most of LXQt packages that'll mean here - [https://github.com/lxqt](https://github.com/lxqt)

FYI:  *One quick check I perform is looking at the people involved pictures; for the link I provided I recognize five pictures, alas hovering the mouse may help to show names if you're not familiar with pictures people use. If you don't know any of the people it'll be even harder... but LXDE used `pcmanfm` & LXQt used `pcmanfm-qt` where the first five characters are the creator's name, ie. [PCMan]("https://github.com/PCMan") is a developer active in both.*
[I]

Sorry for using a calamares issue as my example; I did a quick look and couldn't find a recent example of a LXQt bug, as most of the issues I've had of late are related to openbox/calamares & non-LXQt packages; at least that I can recall.[/I]

---

