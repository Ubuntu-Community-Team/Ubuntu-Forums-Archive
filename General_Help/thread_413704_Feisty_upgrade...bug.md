---
title: "Feisty upgrade...bug??"
date: 2007-04-19
forum: General Help
---

### Post by Th1eF` on 2007-04-19
trying to update to Feisty and get the following:

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugrepo

---

### Post by billdotson on 2007-04-19
I have no idea man.  Google and see if anyone else is having similar problems.  Try searching this: ubuntu- could not calculate upgrade in google.
By any chance did you uninstall anything that was in the ubuntu-desktop metapackage?  I hear that that can cause errors and cause the upgrade process to be a bit more difficult.  I am by no means an expert of this though.

---

### Post by autocrosser on 2007-04-19
Yes - you need ubuntu-desktop to allow the upgrade. You can also change all your repositories from Edgy to Feisty & use Synaptic or apt-get (only do that if you don't get a answer from insztalling ubuntu-desktop or fiiling a bug against update-manager).

---

### Post by jgordon510 on 2007-04-19
I was having the same problem.  I suspected that it had to do with 3rd-party packages.  I Went into Synaptic, disabled 3rd-parties and uninstalled a bunch of stuff that had been 3rd party stuff (compiz, beryl, cinelerra, and a few other things I can't remember).  I tried upgrading again and it worked.  Wish I could be more specific.

---

