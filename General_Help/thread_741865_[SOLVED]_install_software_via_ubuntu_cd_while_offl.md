---
title: "[SOLVED] install software via ubuntu cd while offline?"
date: 2008-04-01
forum: General Help
---

### Post by Rytron on 2008-04-01
I know that the ubuntu 7.10 cd can be added to the software sources under the 'ubuntu software' and 'third party software' tabs. When you go to the synaptic manager, is it just a case of hit and miss as to what can and cannot be installed via the 7.10 Ubuntu cd? Is there a list of software that can be installed via synaptic while off line and simply using the 7.10 Ubuntu cd? Also one last question; under the ubuntu software tab in software sources diaog box, below where it says 'installation from cd-rom/dvd I have 4 entries of cdrom with Ubuntu 7.10 'gutsy gibbon' - how do I get rid of these repeatig entries?

Thank you.

---

### Post by plucky on 2008-04-01
> installation from cd-rom/dvd I have 4 entries of cdrom with Ubuntu 7.10 'gutsy gibbon' - how do I get rid of these repeatig entries?

You need to edit the sources.list file ```
gksudo gedit /etc/apt/sources.list
``` and remove the entries that look like this > # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

Good Luck

---

### Post by ugm6hr on 2008-04-01
You can see the packages on the CD if you just look through it.

They are basically just the programs included in the LiveCD but not default installed - stuff like GParted.

I wouldn't rely on being able to install much else that is useful.

---

