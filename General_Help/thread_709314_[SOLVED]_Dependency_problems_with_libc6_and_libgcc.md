---
title: "[SOLVED] Dependency problems with libc6 and libgcc1"
date: 2008-02-27
forum: General Help
---

### Post by headbug on 2008-02-27
Hi,

I just managed to break my system and now I hope someone know how to proceed:

I wanted to build the latest release of octave on a gutsy dist. But some packages were too old so I tried to upgrade the packages, among them libc6 and libgcc1

Anyway, I decided to cancel and now I am stuck with a libc6 that I can't configure because it depends on libgcc1 which is not configured, and I can't configure libgcc1 because it depends on libc6,

It's a never ending loop here, how do I proceed?

Regards,
Jonas

---

### Post by y-lee on 2008-02-27
This is a guess but*** Maybe*** you can open Synaptic and go to edit and choose Fix broken packages.

---

### Post by headbug on 2008-02-27
Hmm, actually I'm in andLinux and I don't think I have access to Synaptic, but thanks for the suggestion. Is there any command line equivalent to Synaptic?

I'm not overly concerned, I have a fresh andLinux install and can easily just make a new install and then dist upgrade before I attempt to install octave again. But it would be nice if someone knew how to break out of my infinite dependency loop :)

---

### Post by Fixman on 2008-02-27
> **headbug said:**
> Hmm, actually I'm in andLinux and I don't think I have access to Synaptic, but thanks for the suggestion. Is there any command line equivalent to Synaptic?

I'm not overly concerned, I have a fresh andLinux install and can easily just make a new install and then dist upgrade before I attempt to install octave again. But it would be nice if someone knew how to break out of my infinite dependency loop :)

Can't you try to do a new build of libc6 on your "complete" partition, and put it on your "incomplete" one? Or, I think there libc6 is on Ubuntu CD.

---

### Post by mc4man on 2008-02-27
you could try```
 sudo apt-get install -f
```
or maybe -```
 sudo apt-get install --fix-missing
```

---

### Post by headbug on 2008-02-29
> **mc4man said:**
> you could try```
 sudo apt-get install -f
```
or maybe -```
 sudo apt-get install --fix-missing
```

Hi again, that was the first thing I tried, but with the result that I was told that ~2000 packages was to be upgraded or removed and was I really really sure I wanted to do this?

But now I have reinstalled my system and am currently upgrading to Hardy so I hope everything will be fine from now on!

Cheers!

---

