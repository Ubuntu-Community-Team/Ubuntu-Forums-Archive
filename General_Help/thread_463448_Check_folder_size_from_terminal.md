---
title: "Check folder size from terminal"
date: 2007-06-03
forum: General Help
---

### Post by lamadredelsapo on 2007-06-03
Is there any command to check the size of a folder in the terminal?

---

### Post by dfreer on 2007-06-03
```
du -h
```
Not quite sure on how to get it to report subfolders as well, but it works. try reading the man page for it if you want some more commands.

---

### Post by RedSquirrel on 2007-06-03
```
du -h directory_name
```reports the size of all directories beneath a given directory and the total at the bottom. If you just want a total for that directory, then use

```
du -hs directory_name
```

If you don't provide a directory_name, the current directory will be used.

As suggested, the manpage has all the options.

```
man du
```

---

### Post by lamadredelsapo on 2007-06-04
I'll give it a try, thanks!

---

