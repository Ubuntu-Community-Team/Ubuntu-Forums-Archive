---
title: "zip / find / recursive search problem"
date: 2008-04-10
forum: General Help
---

### Post by chmmr on 2008-04-10
I'm simplifying greatly from the real world case, but I have a directory structure that looks like this:

./default.cfg
./stuff
./stuff/dontwant.zap
./stuff/custom.cfg

I want to create a zip archive file that has all the .CFG files in it, with directories intact, but not the files I don't want (the .zap) file.

I use this command line:

zip -r test.zip -i *.cfg

from the top level dir, to do a recursive search that will include all the files I want.  This fails to recognize the .cfg file in the lower directory, for reasons I can't understand.

I tried a similar thing with the basic find command:

find . -iname *.cfg

and got the same result... cfg file in base dir, but not in the subdirs.  Why is this?  Is there some basic bit of UNIX path recursion lore I'm missing?

---

### Post by BaffledMollusc on 2008-04-10
Looking at the man page, you might need a capital "R", i.e.

zip -R test.zip -i *.cfg

If that's not it... I have no idea.

---

### Post by chmmr on 2008-04-10
Good thinking, but "PKZIP style recursion" gives me the same result.

---

### Post by ryanhaigh on 2008-04-10
In this thread I provide a command to find jpgs and copy them including directory structure, maybe you could use this and add a zip command to the end to zip the resulting dir then delete that directory leaving only the zip.

---

### Post by bodhi.zazen on 2008-04-10
Try quoting your search pattern :

find . -iname "*.cfg"

And then try :

```
find . -name "*.cfg" -print | zip test.zip -@
```

---

### Post by Slim Odds on 2008-04-10
> **chmmr said:**
> ....
I use this command line:

zip -r test.zip -i *.cfg



From within the directory, try this:
```
zip -r test.zip . -i *.cfg
```

---

### Post by bodhi.zazen on 2008-04-10
> **Slim Odds said:**
> From within the directory, try this:
```
zip -r test.zip . -i *.cfg
```

You still need to quote the expression

```
zip -r test.zip . -i "*.cfg"
```

---

### Post by chmmr on 2008-04-10
Aha, adding the quotes did it.  I didn't read the find manpage closely enough:

"Don’t forget to enclose the pattern in quotes in order  to  protect  it  from expansion by the shell."

---

