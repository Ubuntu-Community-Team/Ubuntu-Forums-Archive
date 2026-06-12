---
title: "In &quot;rm -rf&quot; what does &quot;-rf&quot; mean?"
date: 2007-11-09
forum: General Help
---

### Post by enchance on 2007-11-09
In "rm -rf" what does "-rf" mean?

---

### Post by dpar on 2007-11-09
Try this in terminal

> man rm

---

### Post by Maestro23 on 2007-11-09
> **enchance said:**
> In "rm -rf" what does "-rf" mean?

Open a terminal:

> man rm

---

### Post by kebes on 2007-11-09
> **enchance said:**
> In "rm -rf" what does "-rf" mean?

The "-r" switch means "recursive"... which means that the remove operation will go into sub-directories.

The "-f" switch means "force"... which means that it will remove files without prompting for confirmation.

Be careful when using "rm -rf" because it will quickly and irreversibly delete files! For more information on the switches for rm, [see here]("http://unixhelp.ed.ac.uk/CGI/man-cgi?rm").

---

### Post by omrsafetyo on 2007-11-09
is -f implied/default???

I did this once at work.. luckily it was the test system, and no files were needed....

tried ```
rm -r *txe1*
```

and accidentally put a space between the asterisk and the "txe1".  response: <b>error: file or directory txe1 does not exist.</b>

me:  huh??

```
ls -l
```

0 files

:shock:

---

### Post by kebes on 2007-11-09
> **omrsafetyo said:**
> is -f implied/default???
If you use "rm" you should be careful! It will go ahead and delete huge batches of files without confirmation! However the "-f" also means that it will not prompt when deleting read-only files, or files owned by someone else, etc.

---

### Post by enchance on 2007-11-09
> **kebes said:**
> The "-r" switch means "recursive"... which means that the remove operation will go into sub-directories.

The "-f" switch means "force"... which means that it will remove files without prompting for confirmation.[/URL].

I see what you mean. So you can append commands instead of writing them separately instead of "rm -r -f". Thanks.

---

### Post by mahousaru on 2007-11-10
> **omrsafetyo said:**
> is -f implied/default???


It might have been aliased.  type alias to see what short cuts (aka death traps) might have been added.

---

