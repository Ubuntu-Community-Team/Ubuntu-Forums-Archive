---
title: "CUPS server error when trying to add network printer."
date: 2017-01-25
forum: General Help
---

### Post by alexf2294 on 2017-01-25
I can't for the life of me figure out what is wrong here. Whenever I try to ad a new network printer I get a popup that says "CUPS server error." I've attached a screenshot of the error message that I get. Can anyone help me?

---

### Post by gdesilva on 2017-01-25
I would try to access the cups server directly by using the URL [http://localhost:631](http://localhost:631) on a browser. Add the printer from there and you may get a lot better error code which might point to the problem you are having.

---

### Post by alexf2294 on 2017-01-26
That URL doesn't work. Also, I'm new to Linux. Always used windows, but one day it finally pissed me off and I installed Linux.

---

### Post by dragonfly41 on 2017-01-26
If you run this command .. ```
cat /etc/hosts
```

do you see ... 127.0.0.1    localhost

also check logs in [COLOR=#000000]*/var/log/cups *[/COLOR]

---

### Post by alexf2294 on 2017-01-26
Yes I do see that when I run that command.

---

### Post by gdesilva on 2017-01-26
Can you post the output of 'ps -ef | grep cups'

and also the output of 'cat /etc/cups/cupsd.conf'?

---

### Post by alexf2294 on 2017-01-26
> **gdesilva said:**
> Can you post the output of 'ps -ef | grep cups'

and also the output of 'cat /etc/cups/cupsd.conf'?

Nothing was cut off. Each screenshot starts on the line under the last one.

---

### Post by alexf2294 on 2017-01-27
Also, it uploaded them out of order so just check the filename to see what order they go in. (6,7,8,9,10)

---

### Post by gdesilva on 2017-01-27
When you are posting outputs of commands it is far easier to read if you were to just highlight the contents and simply cut and paste them into the reply form and tag them with code tags . It is very difficult to read individual jpeg images!

Anyway, from what I have seen, it appears that for some reason your cups server is not running - in my case, I have the following output

```
root@Kanga:/etc# ps -ef | grep cups
root      7824     1  0 10:00 ?        00:00:00 /usr/sbin/cups-browsed
root      8865  2984  0 10:32 pts/6    00:00:00 grep --color=auto cups

```

This is perhaps the reason why you cannot access [http://localhost:631](http://localhost:631) and also why you cannot define a printer. I would try to run the cupsd daemon on a terminal and see whether that solves the issue.

---

