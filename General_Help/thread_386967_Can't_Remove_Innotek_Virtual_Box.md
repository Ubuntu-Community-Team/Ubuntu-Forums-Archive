---
title: "Can't Remove Innotek Virtual Box"
date: 2007-03-17
forum: General Help
---

### Post by dontgetshocked on 2007-03-17
Innotek Virtual Box is causing me problems and it wont let me remove it. Thru synaptic manager it gives me the error 
E: virtualbox: subprocess pre-removal script returned error exit status 1

And it does not complete the procedure.

Suggestions>

I also tried sudo aptitude update
and also                              upgrade
and tried ap-get update

this did not correct the problem.

---

### Post by zvacet on 2007-03-18
```
sudo aptitude remove program_name
```
If it doesn´t work uninstall it manualy.Look in usr/bin (also etc,home,home hidden folder).

---

### Post by wj32 on 2007-03-18
> **zvacet said:**
> ```
sudo aptitude remove program_name
```
If it doesn´t work uninstall it manualy.Look in usr/bin (also etc,home,home hidden folder).
**Don't** "uninstall it manually". Uninstall it properly. You can't, so, wait for another reply.

---

