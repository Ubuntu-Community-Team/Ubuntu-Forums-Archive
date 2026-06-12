---
title: "Removal of executable bit from flies in multiple dirs?"
date: 2008-03-12
forum: General Help
---

### Post by disturbedite on 2008-03-12
ok here is the situation.  (i'm on kubuntu hardy btw, not that it prolly matters).
a long time ago i accidentally added the executable bit to a bunch of files that didn't need it.  those files are in multiple directories.  (i don't know if this matters, but they're all name similarly: 01.jpg, 02.jpg, etc).  i want to remove it from those files via command line but i don't know how.  i don't want to have to go into each dir & remove the executable bit for all the files in the dir, that would take too long.  i want to remove the executable bit with one command, if possible.

it was recommended to me to try: ```
chmod a-x *.jpg or chmod 666 *.jpg
```this works, but only for single dirs, not multiple dirs.  if i try it with multiple dirs i get:
```
chmod: cannot access `*.jpg': No such file or directory
```is this possible with chmod or some other program?  or would this require a script of some kind?

---

### Post by mannheim on 2008-03-12
You can use the "find" command to do this sort of thing: something like
```

find . -name \*.jpg -exec chmod a-x \{\} \;

```
The backslashes are necessary. But try this on a small duplicate of part of your directory tree first, to avoid making a horrible mistake.

(The command means: find all files and directories in or below the current directory, with name matching *.jpg, and for each one execute "chmod a-x <name>".)

A less cryptic version (more verbose than needed) would be something like:```

for x in `find . -name \*.jpg`; do chmod a-x "$x"; done

```

---

### Post by Oldsoldier2003 on 2008-03-12
> **disturbedite said:**
> ok here is the situation.  (i'm on kubuntu hardy btw, not that it prolly matters).
a long time ago i accidentally added the executable bit to a bunch of files that didn't need it.  those files are in multiple directories.  (i don't know if this matters, but they're all name similarly: 01.jpg, 02.jpg, etc).  i want to remove it from those files via command line but i don't know how.  i don't want to have to go into each dir & remove the executable bit for all the files in the dir, that would take too long.  i want to remove the executable bit with one command, if possible.

it was recommended to me to try: ```
chmod a-x *.jpg or chmod 666 *.jpg
```this works, but only for single dirs, not multiple dirs.  if i try it with multiple dirs i get:
```
chmod: cannot access `*.jpg': No such file or directory
```is this possible with chmod or some other program?  or would this require a script of some kind?

chmod -R  is what you're looking for 
[http://www.linuxmanpages.com/man1/chmod.1.php](http://www.linuxmanpages.com/man1/chmod.1.php)

---

### Post by nick_h on 2008-03-12
Edit:  This will not work - see post below.

Yes, the -R option is the way to go:
```
chmod -R a-x *.jpg
```

---

### Post by mannheim on 2008-03-13
> **nick_h said:**
> Yes, the -R option is the way to go:
```
chmod -R a-x *.jpg
```

No, I think this will still give you a  "No such file or directory". (The command essentially asks chmod to remove the execute permissions from all directories whose name matches "*.jpg" as well as all files and directories below these directories.)

---

### Post by nick_h on 2008-03-13
Thanks for correcting me.  The shell will apply pathname expansion to the *.jpg and hence the effect will be on the current directory.  Removing execute from directories will remove access to them.

The find command you suggested will work.  If the user actually has directories ending in .jpg (unlikely) then they should add -type f to exclude them.

```
find . -name '*.jpg' -type f -exec chmod a-x '{}' \;
```

---

### Post by disturbedite on 2008-03-13
> **mannheim said:**
> You can use the "find" command to do this sort of thing: something like
```

find . -name \*.jpg -exec chmod a-x \{\} \;

```The backslashes are necessary. But try this on a small duplicate of part of your directory tree first, to avoid making a horrible mistake.

(The command means: find all files and directories in or below the current directory, with name matching *.jpg, and for each one execute "chmod a-x <name>".)

thanks so much!  i did exactly that (tested it first).  it worked without any issue whatsoever.

---

