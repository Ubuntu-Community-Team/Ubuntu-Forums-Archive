---
title: "How do I create a file with the names of everything in a folder?"
date: 2016-02-29
forum: General Help
---

### Post by nzdreamer55 on 2016-02-29
Hello everyone,

I would like to create a file that contains a listing of all the files and folder within a folder.  I want to use this file to compare against as time goes on.  The folder that I want to do this to has several layers deep.  I don't need to keep the structure of the folders and files, just a listing of everything all the way down.

I think I need to use the echo command?

Thanks

---

### Post by goofprog on 2016-02-29
find <directory> > list.txt
example
find Desktop > list.txt

---

### Post by sudodus on 2016-02-29
Change directory to that folder, and run ```
find
``` to get file name including the relative path.

Run ```
find | sed 's#.*/##'
``` to strip off the path and get only the file names.

You can sort them by ```
find | sed 's#.*/##' | sort
```

... and redirect to a file

```
find | sed 's#.*/##' | sort > file.txt
```

---

### Post by Dennis N on 2016-02-29
I like this way:

cd to the desired directory, then

```
ls -lR > output-file.txt
```

This will create the output file in the same directory, otherwise include a path.

or skip the cd step and

```
ls -lR [path-to-directory] > output-file.txt
```

paths can be relative or full.

Leave out the **> output-file.txt** to get output to screen.

---

### Post by sudodus on 2016-02-29
If you want only regular files, not links and not directories, you can add the option -type f

```
find -type f | sed 's#.*/##' | sort > file.txt
```

---

### Post by steeldriver on 2016-02-29
... you shouldn't need to use sed (or anything else) to remove the leading pathname components, just use

```

find . -printf '%f\n'

```

See `man find` (in the `-printf` section)

```

              %f     File's name with any leading  directories  removed  (only
                     the last element).

```

---

