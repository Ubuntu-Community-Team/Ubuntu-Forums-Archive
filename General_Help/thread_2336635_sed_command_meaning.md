---
title: "sed command meaning"
date: 2016-09-09
forum: General Help
---

### Post by babakflame on 2016-09-09
Dear Fellows

  Maybe it's not directly related to this forum. However, I have started increasing my knowledge on shell commands so as to run commands in ubuntu terminal:):)

I faced a sed command that can not parse it.

```
 sed -r "s/(cat|dog)s?/ \1 /g"  
```

here, -r means recursive
s means substitution
(cat|dog) means cat or dog
But what does [COLOR=#b22222]_s?_[/COLOR] mean here?
I guess \1 means escape 1 cat or dog.  ([COLOR=#ff0000]what does this do exactly here?[/COLOR])
/g means global.

would somebody plz help me?:P
Regads

---

### Post by vasa1 on 2016-09-09
> **babakflame said:**
> ...
```
 sed -r "s/(cat|dog)s?/ \1 /g"  
```

here, -r means recursive
...

Did you look at **man sed**? It doesn't have "-r means recursive".

And for```
But what does s? mean here?
I guess \1 means escape 1 cat or dog. (what does this do exactly here?)

```read about regex backreferences.

---

### Post by steeldriver on 2016-09-09
No, -r means to use *extended regular expression* syntax

s? means 0 or 1 literal 's' character, making the 's' optional - in other words, (cat|dog)s? matches both singular 'cat' and 'dog' and plural 'cats' and 'dogs'

\1 is a backsubstitution - it refers to the first matched group (i.e. the thing between parentheses) so for example 'dog' in the original text would be replaced by ' dog ' (with a space each side)

Hope this helps - lots more at [http://www.regular-expressions.info/](http://www.regular-expressions.info/)

g does mean global - but not in the sense that many people seem to think ("everywhere in the file") but in the sense of multiple times in a single line (technically, within a single *pattern space*)

---

### Post by CantankRus on 2016-09-09
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] cat test.txt**
dog
cat
bulldogs
dogs
catnip
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] sed -r "s/(cat|dog)s?/ \1 /g" test.txt**
 dog 
 cat 
bull dog 
 dog 
 cat nip
```

---

### Post by babakflame on 2016-09-09
Many thanks from both of you. Especially steeldriver.

 sometimes things are so clear for you guys:popcorn::popcorn:
 But for newbies to shell programming like me not at all.

  For example that /g "global" now makes sense to me to be parsed as "multiple times in single line".

  BTW, special thanks to CantankRus as well.

  Thats why I ask my questions here.

  Many thanks fellows.:KS:KS

---

