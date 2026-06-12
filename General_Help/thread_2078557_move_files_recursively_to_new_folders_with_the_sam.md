---
title: "move files recursively to new folders with the same name as the file?"
date: 2012-10-31
forum: General Help
---

### Post by sohlinux on 2012-10-31
Hi, 

How can I move files recursively to new folders with the same name as the file

example

I have a folder containing 500 files with various names with all the same extension .txt

I need to make 500 new folders with the same names of the files then move the 500 files into those folders.

thanks

---

### Post by drmrgd on 2012-10-31
I think you can do this with a simple parameter expansion and loop, sort of like:

```
#!/bin/bash

for file in file*.txt
do
    dir="${file%.*}"
    echo mv "$file" "${dir}/${dir}.txt"
done
```

A couple notes...change 'file*.txt' to match what you have.  You might just use '*.txt'.  Also, I've left the echo statement in there for testing purposes.  This will show you what would be moved, but not actually do the move.  When you're satisfied with how it's working, just remove the word 'echo' and let it loose.

---

### Post by sohlinux on 2012-10-31
> **drmrgd said:**
> I think you can do this with a simple parameter expansion and loop, sort of like:

```
#!/bin/bash

for file in file*.txt
do
    dir="${file%.*}"
    echo mv "$file" "${dir}/${dir}.txt"
done
```

A couple notes...change 'file*.txt' to match what you have.  You might just use '*.txt'.  Also, I've left the echo statement in there for testing purposes.  This will show you what would be moved, but not actually do the move.  When you're satisfied with how it's working, just remove the word 'echo' and let it loose.


thanks but it doesn't work

I used *.txt

```

mv: cannot move `abc990.txt' to `abc990/abc990.txt': No such file or directory

```

---

### Post by Lars Noodén on 2012-10-31
mv only works if the target directory exists.  Try adding a step to create the directory.

```

#!/bin/bash

for file in file*.txt
do
    dir="${file%.*}"
    test -d "${dir}" || mkdir "${dir}"
    echo mv "$file" "${dir}/${dir}.txt"
done

```

---

### Post by sohlinux on 2012-10-31
> **Lars Noodén said:**
> mv only works if the target directory exists.  Try adding a step to create the directory.

```

#!/bin/bash

for file in file*.txt
do
    dir="${file%.*}"
    test -d "${dir}" || mkdir "${dir}"
    echo mv "$file" "${dir}/${dir}.txt"
done

```

perfect, thanks :)

---

### Post by drmrgd on 2012-10-31
> **Lars Noodén said:**
> mv only works if the target directory exists.  Try adding a step to create the directory.

```

#!/bin/bash

for file in file*.txt
do
    dir="${file%.*}"
    test -d "${dir}" || mkdir "${dir}"
    echo mv "$file" "${dir}/${dir}.txt"
done

```

Good point!  I forgot about checking for that.  Thanks Lars!

---

