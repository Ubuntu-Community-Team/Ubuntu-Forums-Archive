---
title: "Two ubuntu installs?!"
date: 2007-02-11
forum: General Help
---

### Post by MasterOfMuppets on 2007-02-11
I have WXP and Kubuntu Edgy on a laptop, but in the boot screen it looks as if I have 2 linuxes installed and 1 XP...
What's wrong? I didn't install two linuxes :confused:

---

### Post by localzuk on 2007-02-11
You may have only one linux installed but you can have different kernels installed. What are the actual names of the 'linuxes'?

---

### Post by aysiu on 2007-02-11
You probably have regular Ubuntu and then Ubuntu (recovery mode).

---

### Post by dexter on 2007-02-11
That's not an "issue", that's a "feature" ;).

---

### Post by MasterOfMuppets on 2007-02-12
LOL okay :)...
For each ubuntu "installation" I have a normal and a recovery boot.
I had normal ubuntu and then upgraded to kubuntu via apt-get.
The names are identical, except for -10 in one and -11 in another in the version number.

---

### Post by aysiu on 2007-02-12
After you've booted into the more recent kernel (11, I'm assuming), you can remove the old one (10, probably) using Adept or Synaptic and searching for the phrase *linux-image*.

---

### Post by MasterOfMuppets on 2007-02-12
Thanks everybody!
No. 10 was succesfuly removed! :)

---

