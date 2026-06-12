---
title: "Finding a package by a dependency/sub-package name"
date: 2007-05-29
forum: General Help
---

### Post by TheFuzzy0ne on 2007-05-29
Hi everyone. Please excuse the awful title. I can't think of how best to word it.

By shear chance, I came across a tutorial come time ago which detailed how to link a specific dependency (or child app), to a specific package. I bookmarked it, but I have since lost my bookmarks. I'm not entirely sure what I need to Google for, so I'd appreciate it if anyone could shed any light on the subject.

I would like to find the name of the package that "kjobviewer" is a part of. There will no doubt be more packages I need to do the same for.

Many thanks in advance.

---

### Post by phatty420 on 2007-05-29
Have you tried - aptitude search kjob - or - apt-cache search kjobviewer - I personally like aptitude search, but won't return as many, most of the time but the results are more accurate.  If the packae has an 'i' next to it then its installed, if it has a 'p' then its not.

I hope this helps.

---

### Post by zvacet on 2007-05-29
```
 sudo apt-get install apt-file 
```
```
sudo apt-file update
```

---

### Post by TheFuzzy0ne on 2007-05-29
Fantastic! That's exactly what I was looking for. Thanks a lot both of you. :)

---

