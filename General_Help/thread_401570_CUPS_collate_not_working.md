---
title: "CUPS collate not working"
date: 2007-04-04
forum: General Help
---

### Post by Toxygene on 2007-04-04
I've been trying to collate a print job I'm printing, with no luck.

The printer in question is a HP LaserJet 4100 MFP and I'm using this PPD: [http://www.linuxprinting.org/foomatic-db/db/source/PPD/HP/mono_laser/HP_LaserJet_4100_MFP.ppd](http://www.linuxprinting.org/foomatic-db/db/source/PPD/HP/mono_laser/HP_LaserJet_4100_MFP.ppd)

I've tried checking the Collate checkbox in gnome-cups-manager, setting Collate to True via lpoptions and via lpr (lpr -P hp -# 3 -o Collate=True). In each case, instead of getting X number of collated printouts, I get one printout.

For example, printing three copies, with collation, of a three page document should give:
1, 2, 3, 1, 2, 3, 1, 2, 3

However, I get:
1, 2, 3

Removing the collation option results in the expected:
1, 1, 1, 2, 2, 2, 3, 3, 3


What do I need to do to get collation working?

---

### Post by Toxygene on 2007-04-05
I tried another printer today, a Dell 1710n, but I'm still not having much luck. linuxprinting.org said it uses the hpijs driver, but it didn't have a PPD to download. I tried installing the hpijs packages and I wasn't able to find a Dell 1710n option, or a generic hpijs option.

I'm starting to pull my hair out trying to keep all this stuff straight. Cups, gutenprint, foomatic, hpijs... the documentation is so scattered, confusing, poor and not well defined. I really need a hand here.

---

