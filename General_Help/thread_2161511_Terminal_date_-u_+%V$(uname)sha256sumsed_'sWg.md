---
title: "Terminal: date -u +%V$(uname)|sha256sum|sed 's/\W//g"
date: 2013-07-11
forum: General Help
---

### Post by pbcub1 on 2013-07-11
I type in:
```
**date -u +%V$(uname)|sha256sum|sed 's/\W//g**
```
and all I get in return is
```
> 
```
however when I put it in the form I am using it for, it says it is not what they are looking for.
This output is needed for the the Arch Linux registration form. I am wondering if I am missing something here because I have tryed almost every edit to that first line that I can think of to try to get it to work but it is not working. Please someone Help

-David

---

### Post by deadflowr on 2013-07-11
Aren't you missing the ' symbol after the g?
```
date -u +%V$(uname)|sha256sum|sed 's/\W//g'
```
instead of
```
date -u +%V$(uname)|sha256sum|sed 's/\W//g
```

---

### Post by pbcub1 on 2013-07-11
Thank you, got it working, and signed up.
P.S. I guess its your blue moon ;P

---

