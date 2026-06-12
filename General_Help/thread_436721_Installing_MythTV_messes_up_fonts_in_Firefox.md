---
title: "Installing MythTV messes up fonts in Firefox"
date: 2007-05-08
forum: General Help
---

### Post by kernco on 2007-05-08
Has anyone else had this happen?  I just installed MythTV, and I noticed when it was setting up the packages that it was using wget to download files with font names and .exe extensions.  Now Firefox is using a different font and changing the font in the firefox options doesn't seem to change anything.  Does anyone know how to fix this?

---

### Post by Tamale on 2007-12-30
> **kernco said:**
> Has anyone else had this happen?  I just installed MythTV, and I noticed when it was setting up the packages that it was using wget to download files with font names and .exe extensions.  Now Firefox is using a different font and changing the font in the firefox options doesn't seem to change anything.  Does anyone know how to fix this?

i have the EXACT same problem and would like to get my normal bitstrema vera sans fonts back in opera and firefox.  both browsers were never touched.. something in the mythtv package changes them somehow.

---

### Post by saugumas on 2008-02-14
I have this problem too

---

### Post by saugumas on 2008-02-14
SOLVED. This problem is caused by msttcorefonts, just remove it and firefox will again look normal.

---

