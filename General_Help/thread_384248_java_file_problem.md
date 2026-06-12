---
title: "java file problem"
date: 2007-03-14
forum: General Help
---

### Post by geovino on 2007-03-14
here's a screenshot of my problem...
How do I get this to stop coming up. I have to type no then press enter two times to make it go away. I deleted that file and never even installed it.

How can I stop this from coming up every time I install new programs or updates?

---

### Post by zvacet on 2007-03-14
Try this
```
 sudo apt-get remove --purge filename
```
and look in hidden files in home directory and if you find folder of that software delete it.

---

### Post by Ramses de Norre on 2007-03-14
It's like the message says... you tried installing the java-doc package but the doc package itself isn't on the repo server. You need to get it from sun, put it in the right location and run aptitude again.
Or remove the java doc package to get rid of the message without installing the doc.

---

### Post by geovino on 2007-03-14
I went into hidden file and found a sun download manager program that was installed when I was downloading that java file. I have deleted it but that didn't make a difference. Here's the error message:

E: j2sdk1.4-doc: subprocess post-installation script returned error exit status 1

There is also a .java file. Could that be it? Or was that installed with the initial install of Ubuntu? Let me know because I won't delete it unless I know for sure. 

Thanks

---

### Post by geovino on 2007-03-14
> **zvacet said:**
> Try this
```
 sudo apt-get remove --purge filename
```
and look in hidden files in home directory and if you find folder of that software delete it.

I ran that commend and it looks like it purged and deleted the file. Now when I install any program it can complete without error message. Thanks:)

---

