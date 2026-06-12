---
title: "terminal commands to locate files"
date: 2013-07-18
forum: General Help
---

### Post by and0rsk on 2013-07-18
I'm really new to regex and I'm still trying to get the hand of complicated scripting. Goal is to locate every file with the words iTunes with it thats over 5 mb.

I was originally thinking of doing something like:

stat -c %s | locate iTunes | # this would get results over 5000000 bytes grep '[0-9][0-9]'

Obviously I'm not doing this right but I would appreciate some help on this.
Also any resources that are particularly good in understanding regex would be really appreciated.

Thanks

---

### Post by HiImTye on 2013-07-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
if your files are static then locate is ok
```
locate '[iI][tT]unes*' | while read f; i=$(stat -c %s "$f"); echo "$f: $i"; done | grep "5000000$"
```
if they've changed recently then use find instead
```
find /path/to/folder -iname '[iI][tT]unes*' -exec 'i=$(stat -c %s {}); if [ "$i" -gt 5000000 ]; then echo {}; fi' \;
```
you might want to check my work, I'm tired ;)

---

### Post by Vaphell on 2013-07-18
one can force database refresh for *locate *with *sudo updatedb*

---

### Post by steeldriver on 2013-07-18
You don't need to pass the find output to stat, you can test the size as part of your find command e.g. if it is files whose *name* contains iTunes that you want to find (not clear from your original post)

```
find . -name '*iTunes*' -type f -size +5000000c
```

Note that -name only matches the file portion of the name - not the directory path. If that's not what you want then post back with more details of exactly what you are trying to achieve.

---

