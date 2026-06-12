---
title: "Bash script to copy all files to another folder"
date: 2008-05-10
forum: General Help
---

### Post by sourabhbora on 2008-05-10
Hi,
 I am trying to write a script which copies all files starting with a number (say 89 ) to another directory.
(part of a much more complicated script)
For example:
 To copy files like 
    89_temp.html
 
i=89
command="cp -r ~/"$i_"*   ~/newDestination"

The above does not work. The reason can be understood if you do a 

   [COLOR="Red"]echo $command[/COLOR]
 
Instead of printing
 cp -r ~/89_* ~/newDestination

It lists all the files in my home directory

Its like giving 
     [COLOR="SeaGreen"]ls ~/[/COLOR]
command.

As an alternative, I tried using "find" with -exec cp 
But, find searches through all subdirectories, but I want to copy only top level files.

Thanks for your time
Sourabh

---

### Post by Monicker on 2008-05-10
You could use the -maxdepth option with find.

```
-maxdepth 1
```

---

### Post by sdennie on 2008-05-10
The reason your original command isn't working is because you aren't balancing your double quotes correctly and the _ is considered part of the variable name.  Try this:

```

cp -r ~/${i}_* ~/newDestination

```

---

