---
title: "Using procmail with fetchmail in edgy 6.10"
date: 2006-10-28
forum: General Help
---

### Post by kwrxxx on 2006-10-28
I just installed 6.10 and I have installed fetchmail and procmail along with the .fetchmailrc .procmailrc in my home directory. When I run fetchmail procmail is not called. I have setup logging for both programs and there is no log file written for procmail and email is not filtered. Where should I look to solve this problem?

Beginning of .procmailrc
```

LOGFILE=$HOME/fetchlog/log-procmail-`date +%m-%y-%U`
VERBOSE=no
PATH=/usr/local/bin:/usr/bin:/bin:/sbin:/usr/sbin:/usr/local/sbin:$HOME/bin

```
.fetchmailrc header
```

set postmaster "username"
set logfile $HOME/fetchlog/mailfetch-log

```


TIA
:???:

---

### Post by PriceChild on 2006-10-29
*moves*

---

