---
title: "installing kompose in kubuntu"
date: 2007-02-14
forum: General Help
---

### Post by alfios on 2007-02-14
hi all

trying kubuntu and since my graphics card wont support XGL, i'm trying to at least get Kompose. i ran:

"sudo aptitude install kompose" 

and got this as a reponse:

"No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used."

any ideas? thanks 

alfio

---

### Post by Arisna on 2007-02-14
If you've just installed Kubuntu, chances are you don't have the Universe or Multiverse software repositories enabled.  If you open Adept Manager, the GUI package manager, you can easily uncomment the appropriate lines to get them through View -> Manage Repositories.  Kompose is in the Universe repository, which means it does not get extensive security auditing by the Ubuntu team.  The multiverse repository includes software that is non-Free (as in Freedom).

---

### Post by alfios on 2007-02-14
that did it, thanks! i looked on psychocats.net and followed instructions, not too bad (not sure it makes all that much sense to me yet) but i did it. 

alfio

---

