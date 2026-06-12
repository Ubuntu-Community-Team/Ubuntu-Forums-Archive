---
title: "unzip a bunch of x.zip files at once"
date: 2005-10-20
forum: General Help
---

### Post by matthew on 2005-10-20
Can I use the unzip command on a batch of files at one time?

I have over 100 fonts in a folder, but some kind person decided to save space and zip them all individually. I know how to use the unzip command for one file at a time, but that seems tedious. Is there a way to use it and process the whole batch at once?

BTW, these are in a /home/temp directory so I have full permissions without needing root access

I tried
```
unzip /home/temp/*

unzip /home/temp/*.zip
``` and got
```
unzip:  cannot find or open /home/matt/font/*, /home/matt/font/*.zip or /home/matt/font/*.ZIP.

No zipfiles found.
``` 
I also tried changing to the directory they are in and typing
```
unzip *

unzip *.zip
``` and got
```
caution: filename not matched:  1942_report.zip
caution: filename not matched:  4990810.zip
...etc
``` 
Is this command batch-capable? If not, is there another that is?

---

### Post by KnottyMan on 2005-10-20
Bash script will do it.

Open Terminal, cd to dir, for i in *.zip do ; unzip $i ; done

---

### Post by matthew on 2005-10-20
Doesn't seem to like unzip in the script.
```
$ for i in *.zip do ; unzip $i ; done
bash: syntax error near unexpected token `unzip'
$
``` or
```
$ for i in *.zip do
> unzip $i
bash: syntax error near unexpected token `unzip'
$
``` but if I
```
$ unzip groovy.zip
Archive:  groovy.zip
  inflating: Groovy.ttf
$
``` That works just fine. Bash just doesn't seem to like unzip in a script and calls it an "unexpected token." Am I missing something obvious here?

---

### Post by KnottyMan on 2005-10-20
ah, my bad


for i in *.zip ; do unzip $i ; done

condition ; do action ; done

---

### Post by matthew on 2005-10-20
That did it. Thanks! I'm just getting started with bash and scripting so I appreciate the mini-lesson as well.

---

### Post by washegon on 2006-10-08
any way to unzip each archive into it's own folder while doing a batch unzip?

---

### Post by hikaricore on 2006-11-10
breaks if filenames have spaces.

> for i in *.zip ; do unzip "$i" ; done   

solves this issue

---

