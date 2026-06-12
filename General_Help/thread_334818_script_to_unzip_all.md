---
title: "script to unzip all?"
date: 2007-01-09
forum: General Help
---

### Post by paridoth on 2007-01-09
i have a folder that contains hundreds of other folders, each one containing a single zip file, is there a script or some other way that i can, in one action, have all the zips in this folder extract themselves to a single folder?

---

### Post by lotheac on 2007-01-09
cd to the folder you're talking about and do this.
```
mkdir files && find . -iname '*.zip' -exec unzip {} -d files \;
```
It should create a folder called files and extract the zip files into it.

---

### Post by kidders on 2007-01-09
Hi there,

Unpacking multiple archives to a single directory is not trivial, since most archive formats (including ZIP) support the storage of path-related information. In addition, it would be hard to deal gracefully with multiple identical filenames.

In any case, something like **find -iname *.zip -exec unzip {} \;** ought to unpack your files for you. Hypothetically, were none of your archives to contain duplicated filenames, or other archives, you could recursively "rm" all the ZIPs and "mv" whatever's left to a single location.

**Edit:** Oops... I'm too slow!

---

