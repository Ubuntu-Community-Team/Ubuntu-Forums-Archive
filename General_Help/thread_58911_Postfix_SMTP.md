---
title: "Postfix SMTP"
date: 2005-08-22
forum: General Help
---

### Post by musther on 2005-08-22
I've been trying to set up postfix, I'm a bit new to it, and read somewhere that by default it only listens on localhost, how do I get it to listen for SMTP traffic from the network?

Cheers!

UPDATE:

I just found this page:

[http://www.petersblog.org/node/839](http://www.petersblog.org/node/839)

which is all well and good, but the lines refered to don't exist, and the one I'm asked to replace them with does, but postfix still isn't listening on port 25, I've tried telnetting on 25 and the connection is refused.

---

### Post by mcmuffy on 2005-08-22
Try installing the webmin module of postfix, it makes life a lot easier.

---

### Post by musther on 2005-08-22
There seems to be a problem with postfix itself, I don't know what it could be, but when (on the server) I try telnet localhost 25, I get the following:

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.

And then nothing, the terminal seems to freeze, I can type, but no command does anything.

---

