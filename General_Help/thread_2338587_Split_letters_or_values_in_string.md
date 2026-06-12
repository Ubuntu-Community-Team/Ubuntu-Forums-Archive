---
title: "Split letters or values in string"
date: 2016-09-29
forum: General Help
---

### Post by sed_faster on 2016-09-29
hello everyone,

I found this code, in shell script, on internet: 

```
${word:1:1}
```

and this return the first letter in string saved in variable "word". But I can understand what this double points ":" and numbers one means?

[UPDATE]
I tested this in command line ```
echo ${word:0:1}
``` and I could understand which this interpreted the variable $word which an array. But how this works?

Thanks

---

### Post by steeldriver on 2016-09-29
The two numbers are the *start index* (starting from 0) and the *length *of the substring

e.g.
```

$ word=banana
$ 
$ echo "${word:0:1}"
b
$ echo "${word:0:3}"
ban
$ echo "${word:2:4}"
nana

```

See for example [http://mywiki.wooledge.org/FullBashGuide#Parameters](http://mywiki.wooledge.org/FullBashGuide#Parameters)

---

### Post by sed_faster on 2016-09-30
Hoooo, thanks :)

---

