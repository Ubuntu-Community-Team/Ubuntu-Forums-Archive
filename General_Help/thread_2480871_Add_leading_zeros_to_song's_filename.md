---
title: "Add leading zeros to song's filename?"
date: 2022-11-12
forum: General Help
---

### Post by PDA1 on 2022-11-12
Is there a script or command I can cut and paste into Terminal to add a leading sequential 2 digit number that'll rename all of the files in a directory...such as;

What I have now;

Curious.mp3
Sky.mp3
World.mp3


What I want to see;

01-Curious.mp3
02-Sky.mp3
03-World.mp3

---

### Post by The Cog on 2022-11-13
This should print the commands you want to use.  ```
ls | awk '{print("mv \x27"$0"\x27 \x27"sprintf("%02d-",NR)$0"\x27")}'
```
If that's OK, you can pass the output to bash like this:
```
ls | awk '{print("mv \x27"$0"\x27 \x27"sprintf("%02d-",NR)$0"\x27")}' | bash
```
or change the awk print command to a system command like this:
```
ls | awk '{system("mv \x27"$0"\x27 \x27"sprintf("%02d-",NR)$0"\x27")}'
```

---

### Post by dragonfly41 on 2022-11-13
If a GUI is preferred there is Bulk Renamer.

---

### Post by TheFu on 2022-11-13
I'd use 'qmv' and the visincr.vim addon.  Makes stuff like this trivial, while still being visual.

Another method would be to use a counter in a loop like this:

```
#!/bin/bash

cnt=01

for IN in "$@" ; do
   new=$( printf "%02d" "${cnt}" )
   echo mv "$IN" "${new}-${IN}"
   ((cnt=cnt+1))
done
```
the output could be sent to a file to be run or piped into another shell.  Or just remove the 'echo'.  This could be made shorter by merging 2-3 lines into 1.  Having them separate makes seeing the different parts easier.

That script won't work with files that have spaces, but it does work with normal globbing for other types of files. Run by passing in the filenames or globbed filenames:
```
$ ./script *
```

---

### Post by PDA1 on 2022-11-14
I thank you all for the helpful suggestions.  The code is much too complex for me to understand.  But, I found Krename which works quite well.

---

