---
title: "Tiny Pointy Problem - Directory names are identical due to unrecognized characters"
date: 2013-07-07
forum: General Help
---

### Post by shaolintux on 2013-07-07
I have four directories with names in which it seems there was unrecognized characters? I am stuck with these four "identical" names:

Season ???
Season ???
Season ???
Season ???

How could I target them one at a time to change there names to something workable?

[edit:]

I managed to get the files out of the first one by doing **cd Season* **and then [B]mv * ../Season-1
[/B]But for the other ones I am still stuck, for doing **cd Season*** again only brings me back to the emptied folder of course...

Thank you!
Jonathan

---

### Post by Vaphell on 2013-07-07
you should be able to rename them even without knowing the characters
```
i=0; for d in "Season "*; do mv "$d" "Season $((++i))"; done
```
Season * will match them and from then on their true name, whatever that might be, is in "$d"

---

### Post by dcstar on 2013-07-08
> **shaolintux said:**
> I have four directories with names in which it seems there was unrecognized characters? I am stuck with these four "identical" names:
.......
I managed to get the files out of the first one by doing **cd Season* **and then [B]mv * ../Season-1
[/B]But for the other ones I am still stuck, for doing **cd Season*** again only brings me back to the emptied folder of course...

Thank you!
Jonathan

```
rmdir *
``` will remove any empty folders.

---

