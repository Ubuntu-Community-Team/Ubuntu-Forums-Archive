---
title: "Problems With postfix/dovecot/sasl"
date: 2008-01-10
forum: General Help
---

### Post by Peque on 2008-01-10
Hey THere. 
I have for a year ago installed and setup my mailserver. 
Now I need to move it to another machine, and have really some crazy problems with that. I guess these are related to each other - but cannot find / remember how I did : 
Jan 10 08:26:25 pbj-design postfix/trivial-rewrite[10528]: warning: connect to mysql server 127.0.0.1: Access denied for user 'postfix'@'localhost' (using password: YES)
Jan 10 08:26:25 pbj-design postfix/trivial-rewrite[10528]: fatal: mysql:/etc/postfix/mysql_virtual_alias_maps.cf(0,lock|fold_fix): table lookup problem!!

But taking a look in the DB - should look OK : 
| localhost | postfix          | 0fb45e9a1XXXXXX                          | N           | N  

How Is it to make that change? to allow it to log in ??? 
since mysql -u postfix -p   - ask for the password and logging in ? 
Normally I would have done: 
Grant all on postfix.* to 'postfix' identified by 'PASWORD'; 
And that have updated that ??? But no luck - still the same error? 


And still in the same situation I'll get this error: 
Jan 10 08:26:26 pbj-design postfix/smtpd[10496]: warning: problem talking to service rewrite: Success
Jan 10 08:26:26 pbj-design postfix/master[10440]: warning: process /usr/lib/postfix/trivial-rewrite pid 10528 exit status 1
Jan 10 08:26:26 pbj-design postfix/master[10440]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling

I can remember something about chroot or not. I look through the other machine that I want to move the mailserver from - But nothing rings a bell for me

Can any of you help me here ?? 
Thanks

---

