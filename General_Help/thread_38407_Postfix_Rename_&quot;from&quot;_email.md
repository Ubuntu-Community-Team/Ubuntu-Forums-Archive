---
title: "Postfix: Rename &quot;from&quot; email"
date: 2005-05-31
forum: General Help
---

### Post by infinito on 2005-05-31
Hi!

I want to change the "from" email that postfix adds to local sended emails. I mean, when sending a mail with ```
echo "Mail" | mail user@hotmail.com
``` the user recive a mail from infinito@localhost, and i want it to say "from: [email]infinito@hotmail.com[/email]"

In Debian I just have to add "infinito: [email]infinito@hotmail.com[/email]" at /etc/email-addresses. I know this is a Exim config file, but is there any way to do the same with Postfix?

Thanks in advance!!!

---

### Post by infinito on 2005-05-31
Ok, I'm answering myself, 'cause i found the solution to this...

(1) Create the /etc/postfix/sender_canonical, and add user -> email references like this:
```
$ sudo vi /etc/postfix/sender_canonical

infinito     infinito@hotmail.com
root         infinito@hotmail.com
```
(2) Create /etc/postfix/sender_canonical.db file
```
$ sudo postmap hash:/etc/postfix/sender_canonical
```
(3) Add sender_canonical variable to /etc/postfix/main.cf
```
postconf -e "sender_canonical_maps=hash:/etc/postfix/sender_canonical"
```
(4) Restart Postfix
```
$ sudo /etc/init.d/postfix restart
```
Hope this is usefull for someone...

---

