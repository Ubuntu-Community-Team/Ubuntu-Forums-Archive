---
title: "[SOLVED] command to resolve a full file path"
date: 2007-07-05
forum: General Help
---

### Post by peterx14 on 2007-07-05
I'm writing a shell script that takes an argument that could either be the name of a folder relative to the working directory, or a full file path, e.g.
```
mycommand myfolder/
```
assuming the current directory is **/home/peterx14/** should be handled the same as
```
mycommand /home/peterx14/myfolder/
```
I could probably faff about with testing it with regular expressions and prepending the output of **pwd** where required but what I'm really looking for is a command that will resolve the argument to a full file path. I'm sure there must be one, but I can't find it!

Can anyone help?

---

### Post by jyba on 2007-07-05
Either "realpath" or "readlink -f" should do the job...

```
PATH1="myfolder/"
PATH2="/home/peterx14/myfolder/"

echo $(realpath $PATH1)
echo $(realpath $PATH2)
echo $(readlink -f $PATH1)
echo $(readlink -f $PATH2)
```

...will all return "/home/peterx14/myfolder/"

---

### Post by peterx14 on 2007-07-06
Brilliant! Thanks for that!! :D

---

