---
title: "Simple command / script for zipping files needed"
date: 2006-10-11
forum: General Help
---

### Post by jamespi on 2006-10-11
Hi,

i have a folder with thousands of files in it, and each needs to be turned into it's own individual zip file. ie blahblah.dat needs to be converted to blahblah.zip, and so on for each file. there is no pattern to the filenames, but they all have the same extension. 

is there a simple command or short script that can do this for me?

thanks,
james

---

### Post by tonyr on 2006-10-11
If all the files are simple files (no directories), go to that directory
in a terminal and type ```
**gzip ***
```  It should work if there are
directories anyway.  I think it ignores them, but I'm not sure.  
See **man gzip**.

---

### Post by tonyr on 2006-10-11
ummm...sorry.  That creates .gz files, not .zip files.  If you need
.zip files in particular, this isn't the solution.  The files are
compressed, however, so if compression is all you are after, it
will suffice.

---

### Post by jamespi on 2006-10-11
i specifically need zip files, but i assume there is a plain zip command i could use for that?

---

### Post by tonyr on 2006-10-11
> **jamespi said:**
> i specifically need zip files, but i assume there is a plain zip command i could use for that?

Yes, there is, but the way to use it is not so simple as **gzip**.

I don't know all the ins and outs of **zip**, but here's a simple bash
command that will create blahblah.dat.zip from blahblah.dat.  Unfortunately
it doesn't automatically remove the original.  There may be an option for
**zip** that does that.

Go to the directory in question and type
```

for f in *; do; zip $f.zip $f; done

```

---

### Post by tonyr on 2006-10-11
> **tonyr said:**
> Unfortunately it doesn't automatically remove the original.  There may be an option for **zip** that does that.


The options appear to be -T (check before deleting) and -m (delete
original), so the revised command os
```

for f in *; do; zip -Tm $f.zip $f; done

```

---

### Post by jamespi on 2006-10-12
ah thanks - i get a syntax error when i pasted that line into the command prompt, so i assumed the semicolons were linebreaks and did it a line at a time and it worked. thanks a lot.

---

### Post by jamespi on 2006-10-12
ok i spoke too soon - it seems to be going nuts due to spaces in the file names. can i put it in quotes or something?

---

### Post by jamespi on 2006-10-12
ok i just tried this: (no error this time, even though its all on one line - you dont put a semicolon after "do") 

for f in *; do zip -Tm9 "$f.zip" "$f"; done

and it works fine

---

