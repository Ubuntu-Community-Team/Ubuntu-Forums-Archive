---
title: "need a command to return the directory of a path"
date: 2007-02-20
forum: General Help
---

### Post by gaillard on 2007-02-20
Hi I am just writing a renaming script that has to do some funky renaming but I need to get the directory of the path names I am returning with bash.

Thanks!

---

### Post by Tomosaur on 2007-02-20
Not sure I understand, can you clarify a bit?

---

### Post by gaillard on 2007-02-20
I have a script that is going through a for loop and on each image file it finds I use that whole path to change a substring within it and then rename the file with the changed string.  Problem is part of what I want to put into the file name is the directory name and I just need a command or function that will take a file path and return its directory.. Is there an indirect way to do this?

---

### Post by yabbadabbadont on 2007-02-20
/home/bubba $ dirname $(which fluxbox)
/usr/local/bin
/home/bubba $ which fluxbox
/usr/local/bin/fluxbox
/home/bubba $ basename $(which fluxbox)
fluxbox
/home/bubba $ basename $(dirname $(which fluxbox))
bin

Edit: yet more command line fun

/home/bubba $ dirname $(which fluxbox) | cut -d "/" -f 2
usr
/home/bubba $ dirname $(which fluxbox) | cut -d "/" -f 3
local
/home/bubba $ dirname $(which fluxbox) | cut -d "/" -f 4
bin
/home/bubba $ dirname $(which fluxbox)
/usr/local/bin

---

### Post by gaillard on 2007-02-20
AWSOME.

Thanks you, I don't know how the hell first of all that I didn't know about the dirname command and second the basename command.  If I knew those I probably would have put 2 and 2 together.  OR the cut command, didn't know about that either, I searched teh bash man page and a bunch of others... where can you find this stuff honestly.

Thank you though this is perfect.

---

### Post by gaillard on 2007-02-20
Does anyone know how I can make something simple like,

#!/bin/bash
for j in "$1"*
do
	echo "$j"
done   


That to search recursively instead of only the first directories it hits??

---

### Post by gaillard on 2007-02-20
#!/bin/bash
for j in $(find "$1")
do
	echo "$j"
done 

How about a way to make that not have trouble when there is whitespace in the directory names...

ANYONE?

---

### Post by gaillard on 2007-02-20
Nevermind I didn't think you had to quote the whole darn thing...

#!/bin/bash
for j in "$(find "$1")"
do
	echo "$j"
done

---

### Post by gaillard on 2007-02-20
Actually could someone tell me why this says that the command dirname is getting too long of an argument list?

#!/bin/bash
for j in "$(find "$1")"
do
     echo "$(dirname "$j")"
done

---

### Post by gaillard on 2007-02-20
Ok I have a catch 22.

If I don't use find, I can't use recursion (or at least i don't know how)
If I use find, I can't quote each directory name in anyway.  If I do then the for loop variable just gets assigned one gigantic string.

Anyone?

If find had an option to quote each find it reported then it would be fine, but all it seems to have is the -print0 option that puts a nulll character on the end, but the for loop is still going by whitespace....

---

### Post by yabbadabbadont on 2007-02-21
```
#!/bin/bash
for j in "$(find "$1")"
do
echo "$(dirname "$j")"
done
```

A different method.
```
#!/bin/bash
while read Current
do
echo "$(dirname "$Current")"
done < find "$1"
```
There are always at least ten different ways to do things in Linux.  :D

---

