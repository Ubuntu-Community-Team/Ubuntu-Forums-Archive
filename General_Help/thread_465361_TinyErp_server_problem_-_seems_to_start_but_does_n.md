---
title: "TinyErp server problem - seems to start but does not"
date: 2007-06-05
forum: General Help
---

### Post by leguaan on 2007-06-05
hello,
I´ve just installed apache2 and tinyerp-server + tinyerp-client
created the tinyerp database
**#/etc/init.d/postgresql start**
says *[OK]*
**#/etc/init.d/tinyerp-server start**
says
*Starting tinyerp-server: tinyerp-server.*
but there is no ok...
what's more,
when I 
**#/etc/init.d/tinyerp-server restart**
i get this message:
[I]Restarting tinyerp-server: start-stop-daemon: warning: failed to kill 11599: No such process
tinyerp-server.[/I]
running the client, I cannot login, as connection to server can't be established...
any clue?

---

### Post by instance on 2008-07-19
First make sure you're doing

sudo /etc/init.d/tinyerp-server start

I still had a problem with this. it turns out the password I gave for the Postgre SQL user (terp) could not handle any special characters. The start script did not escape them.

I changed the DB password and got it to work fine.

Also note that the tinyerp-client sometimes needs a restart to check the connection, at least that's what it seems to me.

---

