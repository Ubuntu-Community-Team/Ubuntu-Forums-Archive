---
title: "deleting everything in directory, but not the directory"
date: 2007-03-21
forum: General Help
---

### Post by idynkydnk on 2007-03-21
How can I remove everything from a folder, yet not the actual folder, from the command line?  What about removing everything except one file? except two files?

---

### Post by eXcentra on 2007-03-21
for removing everything, cd into the directory and do *rm **. 
and I don't think there's a way to exclude specific files.. don't know. :|

---

### Post by kpkeerthi on 2007-03-21
if you want to get rid of the subdirectories but keep the current directory...
rm -rf *

---

### Post by idynkydnk on 2007-03-22
Thanks, I should have figured that out myself.  No way to exclude files?

---

### Post by pirothezero on 2007-03-22
> **idynkydnk said:**
> Thanks, I should have figured that out myself.  No way to exclude files?

I wouldn't put it past the system, thats a rather obscure request though. But I believe someone out there would know how to do it if it was possible. Kinda curious myself.

---

### Post by haricharan on 2007-03-22
Suppose you want to delete all the files in a directory just retaining the file named 'immortal' use the following command```
rm -rf $(ls | grep  -v immortal)
```If you want to retain multiple files use backslashed | (OR) operator and the filename in quotes like given below to retain three files 'immortal1', 'immortal2' and 'immortal3'.
```
rm -rf $(ls | grep -v "immortal1\|immortal2\|immortal3")
```I am trying to figure out if the file is within a subdirectory and you want to retain it.

---

### Post by idynkydnk on 2007-03-22
thanks, that works, but the tab doesn't work for the exempt filenames.  I have to type out the whole filename which is pretty time consuming.

---

### Post by stylishpants on 2007-03-22
Both the UNIX command shell and the grep utility provide really good pattern matching capabilities that can help you match a certain set of files for inclusion or exclusion.

If you post your full directory listing (or a representative sample if it's huge) and describe what filenames you want excluded, we could help you figure out some patterns to match the files you want and save yourself some typing.

---

### Post by idynkydnk on 2007-03-22
Here's an example:  Say I have a directory with these files.
dog
cat
horse
reallylonganimalname

if I want to delete everything except reallylonganimalname, I can do ```
rm -rf $(ls | grep  -v reallylonganimalname)
```

but I don't want to type out that long filename.  If I want to just delete that file, I can do ```
rm real **TAB**
``` and the rest of the word will spell out, but when I do ```
rm -rf $(ls | grep  -v real **TAB**)
```

nothing happens

get it?

I hope that makes sense

---

### Post by haricharan on 2007-03-23
yes i agree...the TAB wouldn't work there because you are typing a command within another..
maybe u can just try typing the ls command first( the command within paranthesis) and then use it with rm command

---

