---
title: "Light weight Ubuntu upgrade procedure?"
date: 2013-01-31
forum: General Help
---

### Post by joemartin on 2013-01-31
Hello,  

I never want to do a fresh install of an OS Again.

Currently using a lightweight Ubuntu derivative with Enlightenment.  I want to know which (xubuntu or lubuntu) runs lighter and which has the smoothest, most problem free upgrade procedure from release to release?

Thanks for your time.

---

### Post by ibjsb4 on 2013-01-31
You want no version upgrade problems?  Then go with LTS, its got 5 years of support.

Ubuntu and Xubuntu 12.04 LTS

---

### Post by mörgæs on 2013-01-31
Five years in Ubuntu, three in Xubuntu.

---

### Post by ibjsb4 on 2013-01-31
Did not know that :) thanks

---

### Post by joemartin on 2013-01-31
Lubuntu does not have 3 years support?  

Is the upgrade procedure in xubuntu from lts release to lts release traditionally a smooth one?

---

### Post by raja.genupula on 2013-01-31
99.99% almost all upgrades are succesffull . because before releasing the OS , its has many number of cycles of tests with world-wide ubuntu members.

you can take the same for Ubuntu Flavours too.


Lubuntu not provide its support for three years. you can find here [http://en.wikipedia.org/wiki/Lubuntu#Lubuntu_13.04](http://en.wikipedia.org/wiki/Lubuntu#Lubuntu_13.04)

---

### Post by mörgæs on 2013-01-31
If you find yourself in the 0.01% group, which I do in each and every attempt I have done since 5.10, there is help in the link in my signature. 

A new version of Buntu is released at a pre-determined date no matter if it's buggy or not. It has only happened once that a release was delayed because people wanted more time to debug.

---

### Post by grahammechanical on 2013-01-31
How do you define "lightweight?" I am curious. People say 'lightweight.' What do they mean? Is it:

1) Takes up less disk space.
2) Runs on less RAM.
3) Will give an acceptable user experience with a video card that has 256KB of memory.

What is the specification of a lightweight operating system?

---

### Post by Nr90 on 2013-01-31
I'd say that most people want a lightweight system for either an old laptop/pc or a recent netbook.

Generally they have very little ram (256 mb to 2 gb) and a slow CPU/GPU.
HDD space is less of an issue imo. Even old laptops come with like 60 gb. So the space one would want to save on the install is pretty small imo.

So given your list I would prioritize:
2 > 3 > 1


PS: figures are just my personal experience.

---

### Post by raja.genupula on 2013-02-01
> **grahammechanical said:**
> How do you define "lightweight?" I am curious. People say 'lightweight.' What do they mean? Is it:

1) Takes up less disk space.
2) Runs on less RAM.
3) Will give an acceptable user experience with a video card that has 256KB of memory.

What is the specification of a lightweight operating system?

I do say

1. No
2. Yes
3. Yes

---

### Post by snowpine on 2013-02-01
For best results, wait for the first "point" release (for example 12.04.1) a few months after release, before attempting the release upgrade.

Upgrading Ubuntu is documented here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Mark Phelps on 2013-02-01
> **joemartin said:**
>  ...smoothest, most problem free upgrade procedure from release to release?

IF you follow the forums here over a long period of time and read about "upgrading" (from version to version), you'll find that most (if not ALL) of us who have been at this for a few years advise AGAINST doing an in-place upgrade.

Why?

First, because for an upgrade to be problem-free, two things (at least) would have to be true:
1) Every single app that worked in the old release continues to work (without any changes) in the new release
2) Every single combination of hardware and software that worked OK in the old release was tested with the new release a CONFIRMED to still work OK.

Second (my favorite reason!) -- to this day, Canonical STILL provides no convenient way to roll-back from a new release to the previous release such that, if major problems are found, you can get your old working setup back.

In my experience, the most "problem-free" upgrade procedure would be the same, regardless of the Linux distro used, and is what I do:
1) Install the new version of the distro on a physically different drive from the old version
2) Configure the system to boot into the new version by default
3) At a leisurely pace, duplicate the apps and settings from the old version to the new version.

This way, I ALWAYS have an Ubuntu version that works (the OLD version) while I can take my time fine tuning the new version.

---

### Post by joemartin on 2013-02-02
Settled on Xubuntu 12.04...

Awesome.

---

