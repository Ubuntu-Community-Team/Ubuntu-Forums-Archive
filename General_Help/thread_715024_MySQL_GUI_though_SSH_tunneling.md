---
title: "MySQL GUI though SSH tunneling"
date: 2008-03-04
forum: General Help
---

### Post by jorgepedret on 2008-03-04
Hello people,

This is my case: The mySQL server have only local access so I need to tunnel the connection through ssh. I already made it manually through the console, but I need a GUI because the database is huge and will consume a lot of time to do stuffs though the console. I'm trying Navicat for Linux (as I used to do in Windoze) but I get authentication SSH failure.

What would be your recommendation?

Thanks in advance.

---

### Post by jorgepedret on 2008-03-04
I figured it out, I created a local port forwarding with ssh with this command:

```
ssh -N -f -L [localport]:localhost:3306 user@server.com
```
Where localport is any available local port on you computer, in my case I used 3308

Then from Navicat connected to localhost at port 3308 with the user and password in the remote mysql server, and IT WORKS! it worked perfectly.

Don't know how didn't think of this before.
Thanks for those who read the post!

---

### Post by pichon on 2008-03-05
Is there a particular reason why you just want local access, or are you using ssh tunneling because you don't want any sniffer to be able to read the data you are sending to your database??

Otherwise why don't you just edit the file my.conf (in my case /etc/mysql/my.conf) and comment the bind-address line that binds the access to localhost.

Hope it helps

Pedro

---

### Post by jorgepedret on 2008-03-05
Hi Pedro,

Well I'm working for this company and this is a production level server, thats why there is no direct access from the outside. Thanks for your recomendation anyway.

---

