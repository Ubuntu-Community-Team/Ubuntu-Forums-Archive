---
title: "Conky help"
date: 2007-12-20
forum: General Help
---

### Post by Grout58 on 2007-12-20
I installed conky and its awseome but how can i move it to the upper right corner of my desktop.  I cant find any options for it or config file.  Any help would be great.

---

### Post by kukibird1 on 2007-12-20
Open a terminal  and issue this command  zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc  This will copy a sample config file to your home directory you can then  modify it .
[http://conky.sourceforge.net/]("http://conky.sourceforge.net/") has more info on that 

or open a terminal  and issue this command  conky -a  top_right  will do the same thing but it won't be saved.

---

### Post by rabid9797 on 2007-12-20
in the conkrc file, you can choose for alignment using the words [bottom,top]_[right,left]

ex. 
```
alignment top_right
```

---

