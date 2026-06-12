---
title: "Is this a bug?"
date: 2007-05-12
forum: General Help
---

### Post by Borzo on 2007-05-12
Hi,

I'd like to share an experience i had when upgrading to 6.10 and 7.04.

On both cases the updater changed my UUID's and root entries in GRUB's menu.lst
so i couldn't boot normally after upgrading. The values were wrong and had nothing to 
do with the normal UUID's and root 

I have of course fixed it, but i wonder why is this happening? I would think that the updater should take into account the original menu.lst content, but it sure doesn't look like it. Is this a bug?:confused: 

Borzo

---

### Post by turbojugend_gr on 2007-05-12
I had an issue when installing on an empty disk 7.04, quite identical to what you 're describing. So I can assume it is a bug on the 7.04 grub conf in general (?!)

---

### Post by jerrylamos on 2007-05-12
A stated goal of Gutsy is to concentrate on "polish" on existing packages instead of adding new ones.  I'm not sure what that means, but from my standpoint 7.04 has different bugs on most of the different computers I've tried.  But then again I can do most every application I do on 6.10 anyway if not 6.06 so 7.04 is not "necessary".
If you like bugs, try using the one I'm on now, a pre-Alpha Gutsy 7.10 ......

Cheers, Jerry

---

