---
title: "Reverting apt cache to previous state"
date: 2004-11-17
forum: General Help
---

### Post by wasteed on 2004-11-17
In an attempt to find a decent voip application for my ubuntu
installation, I pointed apt a some debian unstable repository.

After deciding the application was no good, and removing it, I am left with the situation where apt-get keeps telling me
I have 42 packages to upgrade. These packages are basically all X related.

Is it possible to revert what I have done to get back to
my nice clean ubuntu ?

---

### Post by TravisNewman on 2004-11-17
If you remove the sources you added and then run an apt-get update, those won't show up (assuming they were from the repositories you added). If they do show up, you know that they're from the ubuntu repos and that you should download them.

---

### Post by wasteed on 2004-11-17
[QUOTE=panickedthumb]If you remove the sources you added and then run an apt-get update, those won't show up (assuming they were from the repositories you added). If they do show up, you know that they're from the ubuntu repos and that you should download them.[/QUOTE]
 my bad - they are genuine warty security updates.

next time I will check the security announcement forum before I post!

---

