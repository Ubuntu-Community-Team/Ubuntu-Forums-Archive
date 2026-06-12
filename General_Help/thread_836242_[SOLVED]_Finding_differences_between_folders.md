---
title: "[SOLVED] Finding differences between folders"
date: 2008-06-21
forum: General Help
---

### Post by Richard_ on 2008-06-21
I need to find all the differences between 2 folder hierarchies. For example, **folder1** and **folder2** are nearly identical, except that **folder2** may contain some extra files or subfolders. How do I find these differences?

I don't need to worry about differences within individual files, since in this situation if there are 2 identical filenames they will _always_ contain identical data. So basically I just need to find out which files and folders have been added to folder2.

Does anybody have any clue on how to do this?

Advice, as always, is much appreciated. :)

---

### Post by marialice on 2008-06-21
ls -R folder1 > folder1-contents
ls -R folder2 > folder2-contents

(put the names of the files in both folders in a temporary file)

Then compare those:
diff folder1-contents folder2-contents

(and remove the temporary files)
rm folder1-contents folder2-contents

There's probably a more elegant solution, but this should work.

---

### Post by anlag on 2008-06-21
I'd say it's elegant enough, and very easy to put in a shell script which does all the work, outputting the results and getting rid of the temporary files afterwards.

---

### Post by Richard_ on 2008-06-21
Flip, that's clever. Thanks! :-D This is even better than what I was hoping for; now I can pass it through some other checks too.

---

