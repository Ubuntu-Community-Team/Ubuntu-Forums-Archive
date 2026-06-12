---
title: "bash, file globbing in quotes"
date: 2008-07-05
forum: General Help
---

### Post by Meson on 2008-07-05
(My bash version is 3.2)

I want to run a command similar to the following:
```

base=/some/dir
find "$base/folder_[0-9][0-9]" -maxdepth 0 -type d

```

This should have the effect of finding all folders that are /some/dir/folder_##

The problem is, when I quote the root directory for the find command, the globbing doesn't work.  If I unquote the root directory, $base cannot contain a space.

What to do?

---

### Post by HalPomeranz on 2008-07-05
```

IFS=$'\t\n'
base=/some/dir
find $base/folder_[0-9][0-9] -maxdepth 0 -type d

```

The "IFS=" line I added makes the shell not treat spaces as argument delimiters.  So now you can use the glob unquoted and not have to worry about spaces in your file and/or directory names.

---

### Post by Meson on 2008-07-05
It doesn't seem to work...

```

~$ touch this
~$ touch that
~$ touch "this that"
~$ ls -l this that
-rw------- 1 matt matt 0 2008-07-05 14:34 that
-rw------- 1 matt matt 0 2008-07-05 14:34 this
~$ IFS=$'\t\n'
~$ ls -l this that
-rw------- 1 matt matt 0 2008-07-05 14:34 that
-rw------- 1 matt matt 0 2008-07-05 14:34 this

```

---

### Post by unutbu on 2008-07-05
```
base="/some/dir with spaces"; find "$base" -maxdepth 1 -type d   -print | grep "$base/folder\_[0-9][0-9]"
```

---

### Post by HalPomeranz on 2008-07-05
> **Meson said:**
> It doesn't seem to work...

```

~$ touch this
~$ touch that
~$ touch "this that"
~$ ls -l this that
-rw------- 1 matt matt 0 2008-07-05 14:34 that
-rw------- 1 matt matt 0 2008-07-05 14:34 this
~$ IFS=$'\t\n'
~$ ls -l this that
-rw------- 1 matt matt 0 2008-07-05 14:34 that
-rw------- 1 matt matt 0 2008-07-05 14:34 this

```

It works, but in a non-obvious way:

```

$ touch this that "this that"
$ for i in *; do ls -l $i; done
-rw-r--r-- 1 hal hal 0 2008-07-05 12:09 that
-rw-r--r-- 1 hal hal 0 2008-07-05 12:09 this
-rw-r--r-- 1 hal hal 0 2008-07-05 12:09 that
-rw-r--r-- 1 hal hal 0 2008-07-05 12:09 this
$ export IFS=$'\t\n'
$ for i in *; do ls -l $i; done
-rw-r--r-- 1 hal hal 0 2008-07-05 12:09 that
-rw-r--r-- 1 hal hal 0 2008-07-05 12:09 this
-rw-r--r-- 1 hal hal 0 2008-07-05 12:09 this that

```

Basically, IFS only applies to lines that are being read in by the shell's built-in functions, like "read" or things like the loop construct shown above.  

It doesn't apply to arbitrary command-lines like you were trying.  Imagine how awful that would be-- the minute you set IFS to not include the space character you'd no longer be able to use spaces to delimit arguments on your command lines.

So for your original example, I'd do:

```

IFS=$'\t\n'
base=/some/dir
for dir in `find $base/folder_[0-9][0-9] -maxdepth 0 -type d`; do
     # do something here with each $dir
done

```

---

