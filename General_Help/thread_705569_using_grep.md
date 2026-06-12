---
title: "using grep"
date: 2008-02-23
forum: General Help
---

### Post by apunc1 on 2008-02-23
how do i used grep to search for words that end in "ssess" in a directory?
for instance, if i have the directory dict/words, how do i use grep to find words in the directory that in end ssess?

if i have the directory poems/shakespeare that contains .txt files of shakespeare plays, how do i search the shakespeare directory for the words "you" or "me"

thanks.

---

### Post by rapiscan on 2008-02-23
use ```
man grep
``` to see all the options you have available to you.

In this case, if you're already in the desired directory you would do:

```
grep you *.txt
```
Where 'you' is your search term.  You can also do this, to display the line number for each search result.
```
grep -n you *.txt
```
grep also supports regular expressions (see the man page), which will provide more powerful searches.

---

### Post by rapiscan on 2008-02-23
Here's a good little overview of regular expressions in grep:
[http://www.robelle.com/smugbook/regexpr.html](http://www.robelle.com/smugbook/regexpr.html)

---

### Post by apunc1 on 2008-02-23
thanks for the resource

how would i combine some of the expressions together?
how would i find words in dict/words that begin with sm, have an a or i in them and have l as the next letter?
so far i can only do grep ^sm dict/words

---

### Post by rapiscan on 2008-02-23
Something like this:

```
 grep -e ^sm.*[ai]l dict/words/* 
```

The -e tells grep to use extended regular expresions.  As you know ^sm means that the line has to start with sm.  The .* means that anything can follow the sm.  The [ai] means a or i.  And of course l is required, since we want an a or i to be followed by the l.

---

### Post by ghostdog74 on 2008-02-23
> **apunc1 said:**
> how do i used grep to search for words that end in "ssess" in a directory?
for instance, if i have the directory dict/words, how do i use grep to find words in the directory that in end ssess?

you  want to find words in the directory that end in ssess??
```

ls *ssess

```

> 
if i have the directory poems/shakespeare that contains .txt files of shakespeare plays, how do i search the shakespeare directory for the words "you" or "me"

thanks.
If you want to search the directory for files that have words "you" or "me"
```

ls | egrep "you|me"

```
or just do it 2 times
```

ls *yes*
ls *me*

``` 
or use find
```

find /path -type f  \( -name "*yes*"  -o -name "*no*" \) -print
[/code

If you want to search INSIDE the files
[code]
egrep "you|me" *.txt
awk '/you/ || /me/{print FILENAME}' *.txt

```

---

