---
title: "File Roller / Archive Manager Problem"
date: 2008-04-29
forum: General Help
---

### Post by abuakel on 2008-04-29
I didn't know where this question would fall, so I decided to put it in General.

I've never had a problem with extracting .rar files in Gutsy but for some reason, when I tried extracting .rar for the first time in Hardy (I think), I got this error:


Could not open "GC.Y.A.H.pks.rar"

Archive type not supported.


The file, as you can gather from above is called: GC.Y.A.H.pks.rar
At first I thought it wasn't working because of all the periods throughout the name, but that's never stopped it before, so I'm clueless right about now :confused:

---

### Post by zvacet on 2008-04-29
```
sudo apt-get install unrar p7zip p7zip-full
```

Right click on archive and **unpack here**.

---

### Post by abuakel on 2008-04-29
It worked flawlessly, thank you! :)

---

### Post by talking Llama on 2008-04-29
Hey I'm having the same problem and when I ty the above sudo apt-get it says this:
"Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate"
Any help?

EDIT: Never mind I got Ark Unpackager and got unrar-free...

---

