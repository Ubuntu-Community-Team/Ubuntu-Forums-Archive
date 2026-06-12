---
title: "Link Trash to wine programs"
date: 2007-05-28
forum: General Help
---

### Post by maestrobwh1 on 2007-05-28
Is there a way to get apps running under wine to delete files to the trash?  I am using XnView for example, and it is set up to "delete files to trash" but in reality they are just "gone."

Looked in my .wine directory in case I was missing something.  Nope.  No trash there.  I generally don't mind, and don't use wine programs excessively, but when I do, the safety net would be nice.

---

### Post by cookies on 2007-05-28
They most likely go to whereever Windows keeps the recycle bin contents. *Who knows where that is.

So, they are SOMEWHERE in the vastness of ~/.wine

---

### Post by blacksadness on 2007-05-28
look for a RECYCLED folder in drive_c that's where in theory Windows should keep the recycled files of drive c havn't tried in wine though.
if you find it, try and convert it to a link of the trash, i believe .Trash in the user directory

---

