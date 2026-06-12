---
title: "Regex help"
date: 2012-12-27
forum: General Help
---

### Post by JCM_Pico on 2012-12-27
Hello,

I'm tring to use regex to remove some portion of text in a txt file... but i'm not being able to make sed work with it...

Attatched is a print screen of the the find fuction in kate, showing that the regex works...

However when I ty to use this code it does nothing...

```
sed -i 's/(2011)\-(12)\-([0-9][0-9])( )([0-9][0-9])\:([0-9][0-9])/( )/g' 201112.TXT
```

Any help?

---

### Post by steeldriver on 2012-12-27
sed is going to treat all those parentheses literally - also afaik the escapes are not necessary for '-' or ':'

try without them e.g.

```
$ echo 2011-12-13 14:15 | sed 's/2011-12-[0-9][0-9] [0-9][0-9]:[0-9][0-9]/replaced/g'
replaced
```

---

### Post by JCM_Pico on 2012-12-27
It worked 

Thank you very much =)

---

