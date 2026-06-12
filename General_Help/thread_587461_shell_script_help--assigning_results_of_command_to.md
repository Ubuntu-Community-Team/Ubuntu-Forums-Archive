---
title: "shell script help--assigning results of command to a variable"
date: 2007-10-22
forum: General Help
---

### Post by speckman on 2007-10-22
I'm trying to write a shell script to download the latest SOHO sun image and make it my desktop picture.

so i want to do something like this:
```

a="http://soho.nascom.nasa.gov/data/realtime/eit_304/1024/20";
b='date +%y%m%d';
c=".zip";

wget $a$b$c;

```

this doesn't work.  
if I do
```
$a$b$c

```
I get this:
> bash: [http://soho.nascom.nasa.gov/data/realtime/eit_304/1024/20](http://soho.nascom.nasa.gov/data/realtime/eit_304/1024/20)**date**: No such file or directory



well, it appears as if $b will always call "date +%y%m%d"
how do I assign the result of that date command to a variable?

---

### Post by kast on 2007-10-22
try 

**b=`date +%y%m%d`;**

---

### Post by speckman on 2007-10-22
yup!  thanks!

---

### Post by kast on 2007-10-22
No prob!

---

