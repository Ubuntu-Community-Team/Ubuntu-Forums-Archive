---
title: "couchpotato"
date: 2022-07-09
forum: General Help
---

### Post by jgw on 2022-07-09
I'm having a problem with a program called couchpotato.  It used to have a forum but I can no longer find one active.  Its strange because couchpotato is not old and has updates.  Anyway, in the hope that somebody can help me:

[HTML]couchpotato.service - CouchPotato application instance
     Loaded: loaded (/etc/systemd/system/couchpotato.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: exit-code) since Sat 2022-07-09 11:53:18 PDT; 670ms ago
    Process: 19660 ExecStart=/var/lib/CouchPotatoServer/CouchPotato.py (code=exited, status=217/USER)
   Main PID: 19660 (code=exited, status=217/USER)
[/HTML]

As far as I can tell it has something to do with the name.

Thank you ...........

---

### Post by sudodus on 2022-07-09
The HTML text shown is not a typical error or warning, and might as well only show that everything is normal.

You must explain better what is wrong, what you would expect instead of this, and when it happens. Maybe you can also remember and describe if something has happened, that might cause the problem.

---

### Post by Holger_Gehrke on 2022-07-09
"Not old and has updates" ? At least not in an open way ... The Github linked from [https://couchpota.to](https://couchpota.to) says the owner has archived the repository and the last update (v. 3.01) was in 2015.

Holger

---

### Post by jgw on 2022-07-09
Apologies, left off the problem.      
couchpotato.service - CouchPotato application instance
     Loaded: loaded (/etc/systemd/system/couchpotato.service; enabled; vendor p>
     Active: activating (auto-restart) (Result: exit-code) since Sat 2022-07-09>
    Process: 11204 ExecStart=/var/lib/CouchPotatoServer/CouchPotato.py (code=ex>
   Main PID: 11204 (code=exited, status=217/USER)

That was the status of the program.  It turns on and then immediately turns off.  If I look for (code=exited, status=217/USER) there are some returns but none of them make any sense to me. 

I can start it with "python2 /var/lib/CouchPotatoServer/CouchPotato.py" but when I start it with: "service couchpotato start" I get the problem above.  

Again - my apologies!

---

### Post by jgw on 2022-07-09
I know about that one on github as I have been there.  That's the really strange thing.  You can download a rather new program but can talk to anybody about it.  Its VERY strange!  (but the program works.

---

