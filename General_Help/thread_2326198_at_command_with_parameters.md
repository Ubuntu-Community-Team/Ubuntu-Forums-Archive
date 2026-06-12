---
title: "at command with parameters"
date: 2016-05-29
forum: General Help
---

### Post by holaina on 2016-05-29
Hello,

My probleme is with the at command, i try to add some parameters, and this generat a syntaxe error :confused:
here is my command : 
*at  $(date -d "$9 $8" "+%H:%M %m/%d/%y")  -f email.sh $1 $2 $3*, I tried also *at * *$(date -d "$9 $8" "+%H:%M %m/%d/%y")  -f email.sh "$1 $2 $3"*, but it give the same probleme

error : syntax error. Last token seen: t
Garbled time
(it work without parameters)
have you got any idea about this ? il looked for this a lot, il didn't find any example whitch use at with parameters :(
thank you in advance :D

Regards

---

