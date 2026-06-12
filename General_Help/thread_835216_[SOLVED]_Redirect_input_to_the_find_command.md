---
title: "[SOLVED] Redirect input to the find command ?"
date: 2008-06-20
forum: General Help
---

### Post by KaliVoid on 2008-06-20
Hi

Can i redirect input to the find command ?

Can i redirect the input to a specific option ?

when i try ```
find . -type d -name < text.file
```
or just ```
find . < text.file
```
i only get a listing of all the directories.
the text file was generated in another Linux machine with the command "ls -1".

Thanks.

---

### Post by mike2357 on 2008-06-20
I don't think re-directing input to find will work in the way you're trying to do it.  If I understand what you're trying to do, the following script might work:

#!/bin/sh
for i in `cat text.file`
do
find . -name $i -print
done

The script reads lines, one at a time, from text.file and runs the find command on that line.

Good luck.  Let me know if it works.  If not, we'll try something else.

---

### Post by KaliVoid on 2008-06-20
It works :) ,exactly the output i was looking for.
So simple just a "for" loop, i guess its time for me to dig into some script tutorials.

Thank you.

---

