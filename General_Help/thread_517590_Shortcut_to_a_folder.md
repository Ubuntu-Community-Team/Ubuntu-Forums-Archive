---
title: "Shortcut to a folder?"
date: 2007-08-04
forum: General Help
---

### Post by Spaceomega on 2007-08-04
I've been trying to make a shortcut to a folder using the following command on a launcher;

```
nautilus /windows/Documents and Settings/Owner.OMEGA.000/My Documents
```

I think the spaces in the "Documents and Settings" & "My Documents" screw it up; anyway to fix this?

---

### Post by TBerben on 2007-08-04
You need to escape the spaces with backslashes... So "Documents and Settings" becomes "Documents\ and\ Settings"

That seems like a lot of work, but fortunately, you can type part of the path, then hit tab and have bash complete the name for you (including escapes) :D

---

### Post by Spaceomega on 2007-08-04
> **TBerben said:**
> You need to escape the spaces with backslashes... So "Documents and Settings" becomes "Documents\ and\ Settings"

That seems like a lot of work, but fortunately, you can type part of the path, then hit tab and have bash complete the name for you (including escapes) :D

I just went in and manually edited instead of retyping it all.

Thanks for your help :)

---

