---
title: "cannot find suitable command line tool"
date: 2007-10-31
forum: General Help
---

### Post by happymellon on 2007-10-31
Not directly Ubuntu related, but I'm trying on my Ubuntu laptop (and it is Linux related, and I am putting it in general :) )

I am outputting the results of a head of a file to a variable for a script, but the file always has spaces in front of the characters that I want to assign it so $var never seems to get populated. Is there a command to strip the excess spaces from in front of a string so when I run:

head -n1file.txt|var=

It actually populates the var? 

Thanks

EDIT:
Doh, I mean reading in a file to a variable generally really, the stripping of the spaces would be my next task. But running "head -n1file.txt|var=" doesn't do anything because it doesn't add the quotes

---

### Post by ruibernardo on 2007-10-31
Try this:

```
var=`head -n1 data`
```

The accents makes the code execute.

---

### Post by happymellon on 2007-11-03
> **epimeteo said:**
> Try this:

```
var=`head -n1 data`
```

The accents makes the code execute.

Yup, does the trick thanks.

---

