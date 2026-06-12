---
title: "move certain files in multipe directories"
date: 2008-04-23
forum: General Help
---

### Post by psykotrol on 2008-04-23
How would I move certain file types from one directory to another?

for example, how would I move all *.jpg files from something like

```
-Desktop
    -lol
        -1
           -01.jpg
           -02.jpg
           -03.jpg
        -2
           -01.jpg
           -02.jpg
           -03.jpg
        -3
           -01.jpg
           -02.jpg
           -03.jpg

```

and so on, to a different directory?

---

### Post by SpaceTeddy on 2008-04-24
the "find" command has a exec on match option which you can use to perform a shell command on any file found via it. 

from your example, do you want the files moved into the same directory ? because that would mean overwriting them... since they have the same filename. or do you want them to be renamed aswell ?

example
```
find . -name "dummy*" -exec bash -c "echo {}" \;
```

this will echo all files starting with dummy to stdout. Note that this is explicitily done through the echo command at the end. the {} is the full path INCLUDING the filename. you can pretty much use ANY command in the quotes that would normally work alone.

how it helps :)

---

### Post by eool on 2008-04-24
> **psykotrol said:**
> How would I move certain file types from one directory to another?

for example, how would I move all *.jpg files from something like

```
-Desktop
    -lol
        -1
           -01.jpg
           -02.jpg
           -03.jpg
        -2
           -01.jpg
           -02.jpg
           -03.jpg
        -3
           -01.jpg
           -02.jpg
           -03.jpg

```

and so on, to a different directory?

i also wanna a script that can do the same thing.
using WinXP, We can write a .bat 
[COLOR="Red"]@for ./ %%c in (*.flv) do copy "%%c" e:\pict[/COLOR]
but In Linux?

---

### Post by justleen on 2008-04-24
> **eool said:**
> i also wanna a script that can do the same thing.
using WinXP, We can write a .bat 
[COLOR="Red"]@for ./ %%c in (*.flv) do copy "%%c" e:\pict[/COLOR]
but In Linux?

```

for files in `find . -name '*.flv'` ; do cp $files /dest/dir/; done



```

or just use find..


```
find . -name '*.flv' -exec cp {} /dest/dir/ \;



```

---

### Post by SpaceTeddy on 2008-04-24
find . -name "*.flv" -exec bash -c "mv {} /dest/dir" \;

[EDIT]
justleen was faster :) same solution tho :) sorry for the double post :(

---

