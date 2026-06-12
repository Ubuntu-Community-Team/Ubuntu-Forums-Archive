---
title: "Applying a diff to a file"
date: 2017-06-23
forum: General Help
---

### Post by John_Patrick_Mason on 2017-06-23
Hi there,

I'd like to apply a diff to a file. The book that I'm learning from recommends creating a diff file by typing the following:
```

diff -Naur original new > patchfile.txt

```

and then typing:
```

patch < patchfile.txt

```

The problem is that, whenever I use the patch command, patch tries to modify new instead of original.

```

patch < patchfile.txt
patching file new
Reversed (or previously applied) patch detected!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch. 3 out of 3 hunks ignored -- saving rejects to file new.rej

```
Here are the contents of both files:
```

cat -A original
This part of the$
document has stayed the$
same from version to$
version.  It shouldn't$
be shown if it doesn't$
change.  Otherwise, that$
would not be helping to$
compress the size of the$
changes.$
$
This paragraph contains$
text that is outdated.$
It will be deleted in the$
near future.$
$
It is important to spell$
check this dokument. On$
the other hand, a$
misspelled word isn't$
the end of the world.$
Nothing in the rest of$
this paragraph needs to$
be changed. Things can$
be added after it.$

cat -A new
This is an important$
notice! It should$
therefore be located at$
the beginning of this$
document!$
$
This part of the$
document has stayed the$
same from version to$
version.  It shouldn't$
be shown if it doesn't$
change.  Otherwise, that$
would not be helping to$
compress anything.$
$
It is important to spell$
check this document. On$
the other hand, a$
misspelled word isn't$
the end of the world.$
Nothing in the rest of$
this paragraph needs to$
be changed. Things can$
be added after it.$
$
This paragraph contains$
important new additions$
to this document.$

```

Your help is much appreciated.

---

### Post by steeldriver on 2017-06-23
I think it's because you still have the `new` file (which therefore looks like an already patched version of `original`) in your current directory:

```

$ ls
new  original
$ diff -Naur original new > patchfile.txt
$ patch < patchfile.txt
patching file new
Reversed (or previously applied) patch detected!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch.
3 out of 3 hunks ignored -- saving rejects to file new.rej

```

```

$ ls
new  new.rej  original  patchfile.txt

```

If you remove the `new` file, you should find that the patch will succeed:

```

$ rm new*
$ patch < patchfile.txt
patching file original
$ ls
original  patchfile.txt

```

---

### Post by John_Patrick_Mason on 2017-06-24
> **steeldriver said:**
> I think it's because you still have the `new` file (which therefore looks like an already patched version of `original`) in your current directory:

```

$ ls
new  original
$ diff -Naur original new > patchfile.txt
$ patch < patchfile.txt
patching file new
Reversed (or previously applied) patch detected!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch.
3 out of 3 hunks ignored -- saving rejects to file new.rej

```

```

$ ls
new  new.rej  original  patchfile.txt

```

If you remove the `new` file, you should find that the patch will succeed:

```

$ rm new*
$ patch < patchfile.txt
patching file original
$ ls
original  patchfile.txt

```

Hah, I see. And it *worked*. But how come I didn't have to move any file in my first experiment?:

```

cat -A file1.txt
a$
b$
c$
d$

cat -A file2.txt
b$
c$
d$
e$

diff -Naur file1.txt file2.txt > patchfile.txt

patch < patchfile.txt
patching file file1.txt

```

---

### Post by steeldriver on 2017-06-24
My guess is that's to do with how patch determines which file you want to patch. Specifically, from `man patch`:

```

       [B]If no original file origfile is specified on the  command  line,  patch
       tries  to figure out from the leading garbage what the name of the file
       to edit is, using the following rules.[/B]

       First, patch takes an ordered list of candidate file names as follows:
       .
       .
       .
       <snip>
       .
       .
       .
       To  determine  the  best  of a nonempty list of file names, patch first
       takes all the names with the fewest path name components; of those,  [B]it
       then  takes all the names with the shortest basename;[/B] of those, it then
       takes all the shortest names; finally, it  takes  the  first  remaining
       name.

```

I think you will find the behavior changes if you simply rename `file1.txt` and `file2.txt` to `original` and `new`

---

