---
title: "Awk"
date: 2008-02-20
forum: General Help
---

### Post by wh1terabb1t on 2008-02-20
Hello,

Not exactly sure if this category is the best to post this question, but I would like to know how to shorten a field variable with awk.  For instance say if I had a file containing first and last names in columns, how would I go about printing the first character of $1 and the in order to concatenate it with $2.  Thanks in advance for any assistance/direction.

Andrew

---

### Post by WedgeHG on 2008-02-20
Probably want to use substr(). From the awk man page:

substr(s,i,n)  substr(s,i)
  Returns  the  substring of string s, starting at index i,
  of length n.  If n is omitted, the suffix of s,  starting
  at i is returned.

So you would do 

```
substr($1,0,1)
```

to get the first letter.

---

### Post by nick_h on 2008-02-20
Yes, but the index starts at 1 rather than 0.  So for example:
```
echo "abc def" | awk '{print substr($1,1,1) " " $2}' -
```
will give the result:
```
a def
```
To read the manual page using yelp, type:
```
yelp man:awk
```

---

### Post by wh1terabb1t on 2008-02-20
Thanks, that did the trick.

---

