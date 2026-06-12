---
title: "request help: learning bash"
date: 2021-11-09
forum: General Help
---

### Post by mringer on 2021-11-09
Please could you kindly point me at a site where I can get reliable
advice about   bash   programming? In particular, advice on good 
practices & how to debug weird error messages? Is every  bash  the
same or do different systems have different bashes? I say "reliable"
because some sites are clearly not: 

[https://tldp.org/LDP/abs/html/why-shell.html](https://tldp.org/LDP/abs/html/why-shell.html)

says

Most short scripts work right the first time, and
debugging even the longer ones is straightforward.


and  [ https://www.linuxtechi.com/compare-numbers-strings-files-in-bash-script/]( https://www.linuxtechi.com/compare-numbers-strings-files-in-bash-script/)

says

```
#!/bin/bash
# Script to do numeric comparisons

var1=10
var2=20
if [ $var2 -gt $var1 ]
    then
        echo "$var2 is greater than $var1"
fi
# Second comparison
If [ $var1 -gt 30]
    then
        echo "$var is greater than 30"
    else
        echo "$var1 is less than 30"
fi

```

One particular point:  some people do & some do not
put    $var   in quotes when testing, e.g:


```
If [ "$var1" -gt 30 ]
```

Please what is the reason for this?

Thank you

---

### Post by philhughes on 2021-11-09
This is a good place to start learning:

[https://mywiki.wooledge.org/EnglishFrontPage](https://mywiki.wooledge.org/EnglishFrontPage)

In general, you should always quote variables to prevent word-splitting. In the example shown, it doesn't matter since the variables are integers and no splitting can take place.

[https://mywiki.wooledge.org/Quotes](https://mywiki.wooledge.org/Quotes)

---

### Post by dragonfly41 on 2021-11-09
Here is another source.

[https://goalkicker.com/BashBook/](https://goalkicker.com/BashBook/)

---

