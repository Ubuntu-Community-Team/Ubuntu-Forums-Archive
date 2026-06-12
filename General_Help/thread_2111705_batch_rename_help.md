---
title: "batch rename help"
date: 2013-02-02
forum: General Help
---

### Post by ronacc on 2013-02-02
I have a directory with a bunch of text files with only the file names ( no extension ) . I need to add a .txt extension to every file . what is the best way to do this ?

---

### Post by nothingspecial on 2013-02-02
Assuming all the files in the directory have no extension and all the files want one

In the directory that contains the files

```
for f in *; do mv "$f" "$f".txt; done
```

If you mean only some of the files then you will need the test ( [[ ) command first.

---

### Post by ronacc on 2013-02-02
that did it . Thank You

---

### Post by sisco311 on 2013-02-02
EDIT: D'oh! nothingspecial beat me to it! 

If you are looking for a GUI tool, then check out:
[list]
 [*]thunar (file manager)
 [*]gprename 
 [*]gnome-commander (file manager)
 [*]purrr 
 [*]pyrenamer 
 [*]gwenrename 
 [*]krename
[/list]

In the CLI there are many ways. On Debian and Ubuntu I'd probably use the Perl based rename command. 

```
cd path/to/dir/where/the/files/are
prename **-n** 's/(.*)/$1.txt/' ./*
```

-n tells to prename to only print the file names which would have been renamed. 

But you can use the rename command from the util-linux package, mmv or you can write your own little script.

---

### Post by nothingspecial on 2013-02-02
> **sisco311 said:**
> edit: D'oh! Nothingspecial beat me to it! 



[attach]230949[/attach]

---

