---
title: "Firefox 3 w. dual boot: strange behavior"
date: 2008-06-27
forum: General Help
---

### Post by sagesparrow on 2008-06-27
I have a dual boot with XP and 7.10.  I have Firefox 3 on both and they share a profile which is on a different partition.  Everything works fine, except after opening FF3 on XP, the next time I open FF3 on Ubuntu I need to agree to the Software License Agreement again.  Then FF3 opens with all extensions, session history intact, favorites, etc.  The only other difference that I have come across is that the settings in Tab Mix Plus addon are changed back to what I guess are the default settings.  This does not happen every time I open FF3, only the first time I open it in Ubuntu after having used it on XP.

When I had FF2, I had a similar problem.  When opening FF3 in Ubuntu after having used it in XP none of the Addons would be loaded.  I would have to go to the file where the shared profile was located, and delete a couple of files - extension cache and extension rdf.  Then all would be in order.  (I did not have to agree to the SLA with FF2).

Can anyone explain this and a solution?  thanks.

---

### Post by jimv on 2008-06-27
Maybe the XP FF writes one of the config files in a format that Ubuntu can't read, so Ubuntu FF deletes it and makes a new one each time.

---

### Post by sagesparrow on 2008-06-27
i would think that others would have this problem in that case.  any idea how would you test that and work around it?

---

### Post by crossedout on 2008-06-28
This type of issue generally occurs if the two FF versions are not identical.  Check the version numbers to ensure they are the same.  That's the only instance I know of where settings reset or add-ons are checked for compatibility each time.

-Xout

---

