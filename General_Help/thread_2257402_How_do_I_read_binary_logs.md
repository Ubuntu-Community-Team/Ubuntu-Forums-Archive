---
title: "How do I read binary logs?"
date: 2014-12-19
forum: General Help
---

### Post by 1clue on 2014-12-19
Hi,

It seems the longer I run Linux, the more binary logs I see.  There must be some way to read them.

Can someone clue me in?

Thanks.

---

### Post by steeldriver on 2014-12-19
Er... what logs? where are you seeing these?

---

### Post by nerdtron on 2014-12-19
Depends on the logs. some programs have terminal commands to specifically read the logs they create.

---

### Post by 1clue on 2014-12-19
Just some examples in /var/log on Ubuntu Server 12.04:
[LIST=1]
[*]atop.log
[*]btmp.log
[*]faillog
[*]lastlog
[*]wtmp
[/LIST]

This is from one box.  In different instances there are a different number of binary logs.

In some cases, can't remember what but will post when I get back to it, you wind up with a lot of binary logs.  One example I can remember is if you use systemd.

IMO these things have always made the log useless, and I've taken steps to disable the thing that made binary logs.  It seems this is becoming the norm though, so I need to figure out how to read them.

---

### Post by steeldriver on 2014-12-19
You can read wtmp and btmp with commands 'last' and 'lastb' respectively

Similarly, lastlog and faillog have their own display utilities - called 'lastlog' and 'faillog'

I don't know about atop.log

---

### Post by schragge on 2014-12-20
atop.log can be read with *atop -r*. See [atop(1)]("http://manpages.ubuntu.com/manpages/trusty/en/man1/atop.1.html").

---

