---
title: "How to find commands by filename"
date: 2008-03-10
forum: General Help
---

### Post by GNUlancer on 2008-03-10
Here's a little yet ****** up script that when given a grep expression (or just a search term) returns all the executables it can find in PATH directories. I thought it would be nice to share it since simple double-Tab in terminal suggests you more than 2000 commands and entering part of filename followed by a Tab only works when you know how the filename starts.


```
#!/bin/bash

# finds commands by filename

for path in $(echo $PATH | tr ':' ' '); do FILES="$FILES $(ls -Al $path/* 2>/dev/null | grep -E -e -??x?????? | tr ' ' "\n" | grep -e /)"; done
for filename in $(echo $FILES | tr ' ' "\n" | grep $@); do EXECS="$EXECS $(basename $filename)"; done
echo $EXECS | tr ' ' "\n" | sort | uniq
```


Put it into a file and set executable permission (via your file manager or chmod a+x filename), then either put it into your home directory, so that you can call it like './filename searchterm' (assuming you are in your home dir now) or, if you want to execute it from anywhere, just like other commands, put it into one of the PATH directories (/usr/local/bin seems logical).

This works on any platform with bash and coreutils installed. Report bugs if you spot any :D

P.S. Oh censorship, forum fun :p

---

### Post by ghostdog74 on 2008-03-11
good effort. however that whole chunk of code can be simplified...
```

find $(echo $PATH|sed 's/:/ /g') -perm /u+x -print

```

---

