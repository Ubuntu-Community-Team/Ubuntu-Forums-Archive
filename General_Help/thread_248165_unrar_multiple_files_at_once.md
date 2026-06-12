---
title: "unrar multiple files at once"
date: 2006-08-31
forum: General Help
---

### Post by n_hendrick on 2006-08-31
now this is the first time I've tried to do something like this, so you'll have to bear with me. I have a rar that has roughly 2000 rars inside the main rar. I want to extract all the little rars from the main rar. Now I've tried to use the n@(file) option but I'm getting a return error from standard output. Basically the error is new line doesn't exist. Now this may seem hokey but I think the rar was compressed under windows so the list of files I'm trying to extract isn't playing nice with linux. Is there a way to extract all those files at once or am I just gonna be stuck extracting each one individually. I hope someone has an answer, maybe even some new software I haven't come by, but if you could help me it would be greatly apprciated.

---

### Post by croak77 on 2006-08-31
Don't know if this exactly what you want, but it will find all *.rar in a folder and unrar them.

```
find -type f -name '*.rar' -exec unrar x {} \;
```

---

### Post by n_hendrick on 2006-08-31
perfect...thanks man./

---

### Post by bluntu on 2006-09-10
Is there a way I can store my files without actually compressing it?

Right now I can select a folder and 'right-click --> create archive --> Rar' but there's no option that allows me to control the compression. What I would like is just store my files into one rar without compressing it.

---

### Post by twizler on 2007-11-06
> **croak77 said:**
> Don't know if this exactly what you want, but it will find all *.rar in a folder and unrar them.

```
find -type f -name '*.rar' -exec unrar x {} \;
```


YEAH BUDDY IT WORKS!!!!  GOT A set of Songs for Frets on Fire -- 

I COULD NOT FIGURE OUT how to unrar multi folders at once -- with unrar. 

YOU ROCK !!!! thanks -- very useful command !!! 

AWESOME!!!

---

