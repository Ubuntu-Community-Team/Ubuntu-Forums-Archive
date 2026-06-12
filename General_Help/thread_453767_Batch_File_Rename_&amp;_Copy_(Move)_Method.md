---
title: "Batch File Rename &amp; Copy (Move) Method?"
date: 2007-05-24
forum: General Help
---

### Post by medicineman24 on 2007-05-24
OK, so I have 1000's of files organized in 100's of folders.  Every folder has contains the diffferent files with the same names.   I am hoping someone can suggest a program or trick or something that will allow me to Copy/Move all these files to the same folder and change their names so that when ordered by name gnome will list the files in the order they were in before. 

 example: (1, 2, 3, 4, 5) (1, 2, 3, 4, 5) (1, 2, 3, 4, 5) --->  (1a, 1b, 1c, 1d, 1e, 2a, 2b, 2c, 2d, 2e, 3a, 3b, 3c, 3d, 3e)

Or something like that.

---

### Post by stylishpants on 2007-05-24
How about this?

```

find test/ -type f  | while read f; do newname=`echo $f | sed 's#/#_#g'`; cp $f copy/$newname; done

```

It makes filenames that are just the full path, with all the / replaced by _.

This should be run from one dir above the dir containing your large file tree ("test/") in this example.  It copies all the files to the "copy/" directory, which you must create beforehand.

---

### Post by medicineman24 on 2007-05-24
ill try

---

### Post by medicineman24 on 2007-05-24
How can I navigate to location of the file tree (one above) when its on a external hard drive ?

Should I copy the file tree to my ubuntu desktop first?

---

### Post by stylishpants on 2007-05-24
You don't have to copy it over first.


Just change test/ to the directory tree you want to modify, and copy/ to the destination directory.  It should just work.

The directory you run it from affects what the files are named in your copy/ directory, so my advice was intended to give you the shortest possible filename.  It will still work from elsewhere.

---

### Post by medicineman24 on 2007-05-24
how do I use spaces in directory in terminal? Edit: Nvm I know "\ ".  But the command returns with "...file is not in the directory" over and over for every file

---

### Post by stylishpants on 2007-05-24
Yes, the command I posted wouldn't handle spaces in the filenames.

You should handle them by putting quotes around the names.  Here's the command with the name strings quoted:

```
 find test/ -type f  | while read f; do newname=`echo $f | sed 's#/#_#g'`; cp "$f" "copy/$newname"; done
```

---

### Post by medicineman24 on 2007-05-24
Thanks so much. It works like a charm. Now I have to let it copy like 5GBs.  ;)

---

