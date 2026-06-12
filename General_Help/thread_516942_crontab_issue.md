---
title: "crontab issue"
date: 2007-08-03
forum: General Help
---

### Post by isharted on 2007-08-03
ok, i have a php script that i use to generate an html statistics page on chat logs.
if i run ```
php /var/www/nitz/logs/genstats.php
``` everything works fine and it generates the page as expected (takes 25 seconds to compute)

here's what i have in my crontab:
```

$ crontab -l
0,10,20,30,40,50 * * * * php /var/www/nitz/logs/genstats.php

```
every 10 minutes, that generates the first half of the page.  it will just stop at some point in the middle of the page.  i am not sure what could be causing this.  to be specific, it is in the middle of a table, each row being a random quote from 20 different people.  it will just stop after one of the rows.  looking at the page source, i don't see any programming error or permissions problem that could be the cause.  i hope i explained this well enough.  does anyone have an idea what my problem is?

this used to be working fine.  at some point it just stopped (possibly when i upgraded to Fiesty).  thanks in advance!

---

### Post by apetresc on 2007-08-03
Wow, that is truly bizarre. I don't see how cron can be responsible, once it launches the command it's not really responsible for the output of that command any more. Could you perhaps post the genstats.php file and a sample log file? I'll see if I can reproduce the error here and maybe find a programming error.

---

### Post by isharted on 2007-08-03
ok, it'll take me a while get that ready, but i'm working on it now

[EDIT] i set up some test data for you, but the problem didn't occur.  i ran the full 24MB log on the test files i set up for you, and it works fine, too.  i'm not exactly sure where my error was, but i currently have a working product.  i assume it was a small change i made to make it independent of my machine.  i'll look into this a lot more.  until then, thank you very much for your time :)

---

### Post by jongkind on 2007-08-18
I experience same kind of issues: a backup script that works good from the command line is only executed for about 25% when started via crontab. After that it just, well, ...stops. No error messages, nothing. I wonder whether more of you have this issue and whether you found a workaround.

---

### Post by ce41635 on 2007-08-20
I just reinstalled a new Ubuntu Server 7.04 and i have the same problem. I solved my problem by removing the verbose parameters.

Example :

#!/bin/sh

set -x ( Remove this line )

tar -cvf file.tar file ( Change the line for tar -cf file.tar file )

---

### Post by jongkind on 2007-08-21
> **ce41635 said:**
> I just reinstalled a new Ubuntu Server 7.04 and i have the same problem. I solved my problem by removing the verbose parameters.



Very good, this worked for me also!

---

