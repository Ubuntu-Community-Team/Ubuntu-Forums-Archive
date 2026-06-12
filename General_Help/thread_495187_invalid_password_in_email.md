---
title: "invalid password in email"
date: 2007-07-07
forum: General Help
---

### Post by neil10 on 2007-07-07
Set up email account first time, put in my password comes up invalid checked password seems correct. Outgoing mail does send but no incoming.    thks    neil

---

### Post by PgR on 2007-07-11
Well the obvious answer is to check the password!

But if that's right, then ensure that you can get a connection to the pop3 server 

```
telnet mypop3server.myisp.com 110
```The 110 refers to port 110 which is the pop3 port.

You should get answer something like 
```
Connected to mypop3server.myisp.com.
Escape character is '^]'.
+OK <98441.1184156235@mail.myisp.com>

```

So if you can get a connection, then check that your username/password are correct.

```
USER myusername
``` should elicit a "+OK" or similar, and ```
PASS mypassword
``` should also get a "+OK" The capital letters are important.
```
quit
```will log you out.

That should show that your servername username and password are all correct, that you have a route to the server, and that there's nothing blocking the relevant port.

---

