---
title: "quick terminal code question, tar batch extract?"
date: 2006-11-07
forum: General Help
---

### Post by Stochastic on 2006-11-07
Hey, I've got a large number of different archives (.tar, .tar.gz, .zip, etc) that I'd like to extract.  Is there a code for the terminal that can extract them all in one or two swoops? maybe something like ```
ls | tar -xjf *
```

---

### Post by quux on 2006-11-07
you can try 

```
find . -name "*.tar.gz" -exec tar xvfz \{\} \;
``` or 
```
for file in *.tar.gz; do tar xvfz $file; done
```

---

### Post by pitkali on 2006-11-07
```
 do tar xvfz $file;
```
This can make harm. You should rather use ```
tar xvzf "$file";
``` (Note the quotes which make it work even if some filenames happen to contain whitespace.)

---

### Post by Stochastic on 2006-11-07
It looks like the easiest way is to open the folder in graphical form, select all the files, right click and choose 'Extract Here' from the menu.  I realize I asked for a command line solution, but I didn't quite understand those commands and copy/paste from them into the terminal didn't give me much success.

---

