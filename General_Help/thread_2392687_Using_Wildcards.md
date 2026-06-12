---
title: "Using Wildcards"
date: 2018-05-24
forum: General Help
---

### Post by pushbike06 on 2018-05-24
Can you use wildcards to specify a range of files in a move or rename operation.
 E.G. I have a directory A of JPG files created with a camera A. I have another directory B of JPG files created with another camera B at another time and place but some of the file names are the same as those created by camera A.
I want to rename or move the camera A files to directory B without overwriting any files.
I thought I could append A to the filename by using mv *.JPG *A.JPG but this does not work.
Is there a method to do this task as a batch operation.

---

### Post by Holger_Gehrke on 2018-05-24
Neither /usr/bin/mv nor /usr/bin/cp can handle wildcards by themselves. It's the shell that processes wildcards into lists of **existing** **filenames** before calling a program. So you can't do what you want to do that way. You can either use 'rename' before moving or use the option '-n'  of cp and mv to stop them from overwriting existing files.'rename' is a bit tricky, because it's really just a thin wrapper around Perl's regular expressions.
```
rename 's/\.JPG$/A.JPG/' *JPG
``` will **s**ubstitute  '.JPG' at the end of the filename (that's what the '$' stands for in this context; the '\' in front of the dot takes away the special meaning (any character) '.' has in a regex  ) with 'A.JPG' for all files named *.JPG.

Holger

---

### Post by pushbike06 on 2018-05-24
Thanks for your reply. I have loaded Thunar File Manager which has the facility to bulk rename according to various selected parameters. This facility also appears as a stand alone application once Thunar File Manager has been installed. I'll give this a go, it has received mixed reviews.

---

