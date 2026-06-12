---
title: "Rename multiple files at the same time"
date: 2014-05-04
forum: General Help
---

### Post by b2748 on 2014-05-04
Hello everybody,

i am new to ubuntu and having problems renaming multiple files at the same time.

On my previous OS (Win) i would mark all files i want to rename and simply press f2 to give all of them the same name.

Ive read that i need to rename it with the terminal using the rename command.

But still i dont understand how to write the correct synthax to do the job. 

The files i want to rename are like this:

test_part001.rar
test_part002.rar
test_part003.rar
....

Now i want to mark all of the files and rename them to "test1", "test2" and so on so that i can extract them (at the moment there is a disorder in the filenames and i dont want to correct it manually).

Results i want to see:
test1.rar
test2.rar
test3.rar
...

I do not understand the syntax shown in the man rename pages: 's/\.bak$//' *.bak


Many thanks in advance

---

### Post by Lars Noodén on 2014-05-04
The syntax is standard perl regular expression.  You'll sometimes see it as PCRE.  The following might do the job.

```

rename -n 's/_part0*([1-9]+)\./$1\./' *.rar

```

The substitution (s) has two parts there : s/one/two/
Part one is the pattern to look for, part two is the pattern to replace the found pattern.
$1 in the replacement stands for the first capture group, as marked by the parentheses in the search pattern.

The manual page 'perlre' should have more info as will this site:
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)

---

### Post by b2748 on 2014-05-04
@ Lars

Thank you for your help =)

It worked fine, but i had to correct it with [0-9]+ because i had over 127 parts and around 10 or more were not renamed.

so ```
 rename 's/.part0*([0-9]+)\./$1\./' *.rar
 
```

did the job =)

But the files are not named as "test". Instead they are named like this "Myoldname.J1.rar", "Myoldname.J2.rar" ...

But its ok for me.

---

