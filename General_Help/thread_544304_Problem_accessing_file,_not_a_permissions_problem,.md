---
title: "Problem accessing file, not a permissions problem, more likely a hardware problem"
date: 2007-09-06
forum: General Help
---

### Post by martijn hoekstra on 2007-09-06
I have a problem accessing a file. It seems to excist in limbo, not there, but not not there either. It is part of the gimp, and because of this broken file I have problems with updates aswell. The information I have available now is the following:

> 
me@my_machine:/usr/share/gimp/2.0/gradients$ ls -l
total 0
?--------- ? ? ? ?                ? CD.ggr
me@my_machine:/usr/share/gimp/2.0/gradients$ sudo rm CD.ggr 
rm: cannot remove `CD.ggr': Permission denied


Can anyone tell my right away what is wrong here, or suggest some diagnostics I can use to get more information?

Thanks.

---

### Post by bettlebrox on 2007-09-06
what does this command say:

file /usr/share/gimp/2.0/gradients/CD.ggr

Is there anything else in the directory?

---

### Post by martijn hoekstra on 2007-09-06
me@my_machine:/usr/share/gimp/2.0/gradients$ file CD.ggr 
CD.ggr: ERROR: cannot open `CD.ggr' (Permission denied)

---

### Post by martijn hoekstra on 2007-09-06
I probably should have noted that it's a Reiserv3 filesystem.

---

### Post by martijn hoekstra on 2007-09-06
might a crosspost in hardware do me any good here?

---

