---
title: "Where/How to extract downloaded programs"
date: 2007-12-24
forum: General Help
---

### Post by NuNn DaDdY on 2007-12-24
I recently downloaded the .tar file for Filezilla to my desktop and I can extract the folder there but I know that isn't where I want to put it.  My question is how do I go about installing the program and which folder would be the appropriate one to put the file's containing folder in. Thanks

---

### Post by 67GTA on 2007-12-24
Right click on the tar package and choose extract. Follow this link for some info on installing from source:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by nick_h on 2007-12-25
The usual place to install software like this is in /opt

---

### Post by zvacet on 2007-12-25
If you want to install opt you must say so

```
 ./configure --prefix=  /opt
                
                   
```

---

