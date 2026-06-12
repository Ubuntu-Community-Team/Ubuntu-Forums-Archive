---
title: "How to identify broken shortcuts?"
date: 2014-06-25
forum: General Help
---

### Post by sameermw on 2014-06-25
I have more than 1000 icons and also there are hundreds of symbolic links(shortcuts) inside a directory with different names, and also there are sub directories too. some of shortcuts are broken, i need to find which shortcuts are broken.

I tried ```
ls -l
``` But it is difficult to use because it takes more time.
  
How do i do that? And is it possible to fix broken shortcuts. Thanks

---

### Post by Dennis N on 2014-06-25
Try this:

In the terminal cd to the the directory to be checked for broken links. Subdirectories will also be checked. Command:
```
find -L ./ -type l
```
will output broken symbolic links only, with paths relative to the working directory.
Note: -type is followed by the lower-case letter l

To send output to a text file named broken-links.txt in your home directory:
```
find -L ./ -type l > ~/broken-links.txt
```

To fix them, you redo the links.

```
ln -sf newtarget linkname
```

---

### Post by sameermw on 2014-06-26
Oh yes, @[COLOR=#000000]Dennis N [/COLOR][COLOR=#000000]according to your idea i done some home works and [/COLOR]when i surf the web i also found this code thanks to another noob like me. 

```
find . -type l -exec sh -c "file -b {} | grep -q ^broken" \; -print
find . -xtype l -exec sh -c "file -b {} | grep -q ^broken" \; -print

```

Second code is much speed than other one. @[COLOR=#000000]Dennis N, [/COLOR]I think your command is better for small amount of symbolic links, By the way thanks for your support.

---

