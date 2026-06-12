---
title: "are you a Python whiz?  how about sockets?"
date: 2007-01-01
forum: General Help
---

### Post by moshuptrail on 2007-01-01
I'm trying to figure out why hpssd.py won't run.  It's started with hplip (HP Linux Imaging and Printing) and should stay running, but it keeps exiting.  I got it to run in debug mode and got the following output:

```
hpssd[13715]: debug: Exception: 95 (Unable to bind to socket)
error: Server exited with error: Unable to bind to socket
```

If you have hplip installed, you might find the source at:
/usr/share/hplip/hpssd.py
I'm pretty clueless trying to read the code.

My question: What possible reasons might it have for "unable to bind..."?

I believe it tries to use port 2207.  As far as I can tell nothing else is using that port.

---

### Post by moshuptrail on 2007-01-01
Nobody?

---

### Post by moshuptrail on 2007-01-01
Anybody?

---

### Post by koenn on 2007-01-01
A socket is a way for processes to exchange information - could be a tcp/ip socket ( a network connection) or a unix socket (a unix inter process communication technique).
When a program is unable to bind to a socket, it's usually that it expects a socket to exist, but it is not there. 

This indicates either a bug, but more likely a configuration error, or something missing in your system. Wild guess : hplip expects some other application to create a soket it can bind to (cups maybe ?) 
you may have to review your setup.

---

### Post by moshuptrail on 2007-01-01
Thanks.  That, at least points me in a direction.

---

### Post by 11hjpphty76lkjj on 2007-01-12
What happens if you run 

/etc/init.d/hplip restart

also run 

tail -f /var/log/messages

then restart hplip again and view the log for any errors. This should give you some idea of what is going on.

A

---

