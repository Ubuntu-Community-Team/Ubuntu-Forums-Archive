---
title: "How to install GNOME EncFS (Cryptkeeper) in Ubuntu 20.04?"
date: 2020-04-29
forum: General Help
---

### Post by davy jones on 2020-04-29
I've upgraded to Ubuntu 20.04 a few days ago and I tried to install GNOME EncFS using the terminal but it doesn't work. Apparently there's no Release file in the repository so the installation doesn't happen. And I learned that there's no version for this software in 19.10 either. Is there a way I can install this? Or is there an alternative that will read files encrypted with Cryptkeeper? I really need this.

---

### Post by davy jones on 2020-05-01
Bump.

---

### Post by davy jones on 2020-05-03
Bump.

---

### Post by davy jones on 2020-05-07
Bump.

---

### Post by davy jones on 2020-05-11
Why is this such a difficult question to answer?

---

### Post by howefield on 2020-05-11
Doesn't seem such a difficult question, probably more a case of no-one who has read your thread has experience of the current state of the package or the inclination to get involved. <Shrug>

[s]You could try grabbing the deb package directly and doing a simulated install with apt, just to check that you won't run into any issues before installing for real. The most recent package is less than a year old so probably a good chance of it working, but the usual caveats of installing packages outside the versioned repositories apply. :)[/s]

Scratch that. > [Ubuntu 19.10 and later are currently not supported due to the removal of the old gnome keyring API]("https://moritzmolch.com/apps/gencfsm/")

---

### Post by davy jones on 2020-05-15
Considering that it's been 7 months since 19.10 came out, should I just assume that Gnome EncFS will simply not be available in any versions of Ubuntu from now?

---

