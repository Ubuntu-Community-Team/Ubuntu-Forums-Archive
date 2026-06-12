---
title: "Cron every mintute?"
date: 2007-08-03
forum: General Help
---

### Post by Ramthebuffs on 2007-08-03
I'm not really sure how to use cron, what I'm trying now is giving me an error on the install saying bad hour.

*/1****/var/www/other/lva.php 

I've seen some where people need to put [root] or something in the command.  Anybody know what I'm doing wrong?

---

### Post by kuja on 2007-08-03
This should achieve the desired effect, assuming that typing "/var/www/other/lva.php"

As for the time, you've got the following, in this order:

minute
hour
day of month
month
day of week

You either us ethe day of month or the day of week, AFAIK, and not both. (or something like that, check "man cron" to be sure) Pick one.

Next after that is the user it's running as (root in this case eh ... unless you want it to run as some other user.), followed by a space and then the command.

So I guess it will look something like this:

* * * * * root /var/www/other/lva.php

and I think that should do it for you.

---

### Post by Ramthebuffs on 2007-08-03
That seems to have gotten rid of the error, but its not running.  Do I need to include a reference to php somewhere in the line so that it is executable?

---

### Post by splintercellguy on 2007-08-03
Mm, I suppose so. Wouldn't hurt to try :).

---

### Post by Ramthebuffs on 2007-08-03
ok all sorted out now.  I had to go into synaptic and install php cli, then I replaced root with php.  I guess I don't have to put a user into the line.

---

