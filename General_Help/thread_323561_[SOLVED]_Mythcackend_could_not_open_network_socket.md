---
title: "[SOLVED] Mythcackend could not open network socket"
date: 2006-12-22
forum: General Help
---

### Post by SPW06 on 2006-12-22
Hello,

I had just gotten the first set of listings and I tried to restart Mythbackend

And got this in reply 

> sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Could not open network socket
.


My IP and port settings are correct, I am running the client and server locally. I don't understand what could be causing this

Can someone help?

Thanks

---

### Post by superm1 on 2006-12-23
Take a look at /var/log/mythtv/mythbackend.log

Any information there?

---

### Post by tripmix on 2006-12-30
I got this same error. Here is my mythbackend.log, sure didn't do me any good.

2006-12-30 13:12:07.374 Using runtime prefix = /usr
2006-12-30 13:12:07.423 New DB connection, total: 1
2006-12-30 13:12:07.429 Connected to database 'mythconverg' at host: localhost
2006-12-30 13:12:07.433 Current Schema Version: 1160
Starting up as the master server.
2006-12-30 13:12:07.459 New DB connection, total: 2
2006-12-30 13:12:07.463 Connected to database 'mythconverg' at host: localhost
2006-12-30 13:12:07.477 EITHelper: localtime offset 1:00:00
2006-12-30 13:12:07.493 New DB connection, total: 3
2006-12-30 13:12:07.494 Connected to database 'mythconverg' at host: localhost
2006-12-30 13:12:07.641 New DB scheduler connection
2006-12-30 13:12:07.642 Connected to database 'mythconverg' at host: localhost
2006-12-30 13:12:07.667 Main::Starting HttpServer
2006-12-30 13:12:07.690 Main::Registering HttpStatus Extension
2006-12-30 13:12:07.697 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-12-30 13:12:07.697 Enabled verbose msgs:  important general
2006-12-30 13:12:07.704 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2006-12-30 13:12:07.706 AutoExpire: Required Free Space: 1.1 GB w/freq: 10 min
2006-12-30 13:12:09.666 Reschedule requested for id -1.
2006-12-30 13:12:09.716 Scheduled 0 items in 0.1 = 0.03 match + 0.02 place
2006-12-30 13:12:09.721 Seem to be woken up by USER
2006-12-30 13:16:58.023 HTTPRequest::ParseRequest - Timeout waiting for request header.

Only bad thing I see is "Timeout waiting for request header". Hope someone know something about this cuz I'm running out of ideas... ](*,)

---

### Post by superm1 on 2006-12-30
> **tripmix said:**
> I got this same error. Here is my mythbackend.log, sure didn't do me any good.

2006-12-30 13:12:07.374 Using runtime prefix = /usr
2006-12-30 13:12:07.423 New DB connection, total: 1
2006-12-30 13:12:07.429 Connected to database 'mythconverg' at host: localhost
2006-12-30 13:12:07.433 Current Schema Version: 1160
Starting up as the master server.
2006-12-30 13:12:07.459 New DB connection, total: 2
2006-12-30 13:12:07.463 Connected to database 'mythconverg' at host: localhost
2006-12-30 13:12:07.477 EITHelper: localtime offset 1:00:00
2006-12-30 13:12:07.493 New DB connection, total: 3
2006-12-30 13:12:07.494 Connected to database 'mythconverg' at host: localhost
2006-12-30 13:12:07.641 New DB scheduler connection
2006-12-30 13:12:07.642 Connected to database 'mythconverg' at host: localhost
2006-12-30 13:12:07.667 Main::Starting HttpServer
2006-12-30 13:12:07.690 Main::Registering HttpStatus Extension
2006-12-30 13:12:07.697 mythbackend version: 0.20.20060828-3 [www.mythtv.org]("http://www.mythtv.org")
2006-12-30 13:12:07.697 Enabled verbose msgs:  important general
2006-12-30 13:12:07.704 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2006-12-30 13:12:07.706 AutoExpire: Required Free Space: 1.1 GB w/freq: 10 min
2006-12-30 13:12:09.666 Reschedule requested for id -1.
2006-12-30 13:12:09.716 Scheduled 0 items in 0.1 = 0.03 match + 0.02 place
2006-12-30 13:12:09.721 Seem to be woken up by USER
2006-12-30 13:16:58.023 HTTPRequest::ParseRequest - Timeout waiting for request header.

Only bad thing I see is "Timeout waiting for request header". Hope someone know something about this cuz I'm running out of ideas... ](*,)
Was this directly when the frontend was connecting to the backend?  Or what made that request header?  Or was this via a upnp device?  
At this point i'd say more verbose logging would be the only way to find out more, but you might have to bring this problem to the myth mailing list given the scarcity of this issue.

---

