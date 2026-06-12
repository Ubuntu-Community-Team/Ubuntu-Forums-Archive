---
title: "what does this mean -&gt; find -name Thumbs.db -ok rm -f {} \;"
date: 2007-09-30
forum: General Help
---

### Post by taisao on 2007-09-30
Just google out a fast way to delete thumbs created by windows:

```
find /home/user -name Thumbs.db -ok rm -f {} \;
```

I understand most of it but the last 2 ```
{} \
```, I don't understand. Anyone can tell what that mean?

---

### Post by lisati on 2007-09-30
A shot in the dark: look for hidden files?

---

### Post by cwaldbieser on 2007-09-30
> **taisao said:**
> Just google out a fast way to delete thumbs created by windows:

```
find /home/user -name Thumbs.db -ok rm -f {} \;
```

I understand most of it but the last 2 ```
{} \
```, I don't understand. Anyone can tell what that mean?

It is telling the find command to recursively find all the files in /home/user with the name "Thumbs.db" and then ask the user interactively if it is OK to erase them.  If the user enters "y" or "Y", it erases the file.

The -ok option is similar to the -exec option.  The "{}" symbols represent the name of the current file name when used with the -exec and similar options.  The ";" is required to tell find that there are no more arguments to the -exec option.  The ";" would be interpreted by the shell first, though, so it needs to be escaped ("\;") so it is passed to the find command.

---

### Post by taisao on 2007-09-30
oke, thank you for clearing that up

---

