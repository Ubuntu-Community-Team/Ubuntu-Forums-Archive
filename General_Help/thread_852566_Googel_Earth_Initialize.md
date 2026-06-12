---
title: "Googel Earth Initialize"
date: 2008-07-07
forum: General Help
---

### Post by PMTUB on 2008-07-07
I am running 7.10 and recently my Google Earth stopped working.
It hangs in the middle of initializing.
I am running on a Dell 200N which has an ATI Radeon Mobility M6 graphics card.
Any suggestions as to what to look for.
I tried removing and reinstall and Google Earth and backtracking to ver 4.2 but the same result.

Thanks,
Peter

---

### Post by nikgare on 2008-07-10
You probably need to move or delete your .googleearth directory

---

### Post by PMTUB on 2008-07-10
> **nikgare said:**
> You probably need to move or delete your .googleearth directory

I tried that but it made no difference.
Any other ideas?

Thanks,
Peter

---

### Post by nikgare on 2008-07-10
try starting google earth from a terminal and note any error messages

---

### Post by PMTUB on 2008-07-10
> **nikgare said:**
> try starting google earth from a terminal and note any error messages

I found a hint on another forum.
I had to download an copy of libGL.so.1.2, rename it libGL.so.1 and put it in the googleearth directory - worked like a charm.

Thanks,
Peter

---

