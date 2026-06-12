---
title: "Search subfolders using the terminal"
date: 2007-11-11
forum: General Help
---

### Post by enchance on 2007-11-11
How do I search my subfolders using the terminal for a single/multiple files?

---

### Post by bakeneko on 2007-11-11
A quick example:
```
find . -iname *.txt
```
Will search the current folder and all sub-folders for files ending in .txt.  See **man find** for more options.

---

### Post by Dumonde on 2007-11-11
try man find :)
for example:
```
find /some_dir/some_subdir/ -name '*.cpp'
```

---

### Post by weblordpepe on 2007-11-11
Or you can use regular LS
ls * -r

---

### Post by enchance on 2007-11-12
> **bakeneko said:**
> A quick example:
```
find . -iname *.txt
```
Will search the current folder and all sub-folders for files ending in .txt.  See **man find** for more options.

Why is there a "." in between "find" and "-iname"? How about if I want to include hidden files?

---

### Post by logintomyworld on 2007-11-12
Yes thet dot " . " resembles the current directory .

the syntax is


 find  path [ options[parameters]

let u r in /home/sam  folder

find . -iname  "*.txt"

as same as 

find /home/sam -iname "*.txt"

---

### Post by enchance on 2007-12-16
How do I move those files which were found using find to my USB? I use the pipe symbol, right? How does it go?

---

### Post by weblordpepe on 2007-12-17
Can you redirect it to the **rm** command?

I would write a small script. 
A script to use **ls** to output the names of those files to a text file. And then use **tr** to place **rm **in the front of each line in the text file. 

Your outputted text file would then be a shell script you can use to delete stuff. There is most probably a much easier way of doing it though.

---

