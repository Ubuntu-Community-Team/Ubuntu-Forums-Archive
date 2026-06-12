---
title: "Default Firefox Profile Manager Location"
date: 2007-06-03
forum: General Help
---

### Post by revchris on 2007-06-03
I did a search and all I got was: cd  /(firefox directory)/ 

Can someone please tell me where this directory would be located?  I'm trying to add a new profile for testing purposes.

Thanks in advance
Chris

---

### Post by merlinus on 2007-06-03
It is in /home.  Select View Hidden Files (Ctrl-H).  Look for a folder .mozilla, then Firefox, then something akin to

oc7zzzgm.default

Voila!!!

-merlin

---

### Post by Ek0nomik on 2007-06-03
Or via Terminal.  :)

```
cd .mozilla/firefox
```

---

### Post by revchris on 2007-06-03
ok..so I cd to .mozilla/firefox (also tried cd .mozilla/firefox/jumbledmess.default) and then enter ./firefox --ProfileManager and a I get "No Such File or Directory".  I want to setup multiple profiles, what am I doing wrong?

---

