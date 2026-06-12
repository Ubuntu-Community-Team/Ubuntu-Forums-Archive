---
title: "Connect and reconnect to server via ssh using expect"
date: 2008-05-20
forum: General Help
---

### Post by asbjornn on 2008-05-20
I'm accessing the internet by logging on to a server using the command >  ssh -T -l username host But I'm disconnected at random after somewhere between 5 and 30 min of connection. This is terribly annoying so I would like a a program to log me back on as soon as I'm logged of.

I've been told of a program called expect, that might be the solution, but I've got no idea how to use it and not sure where to find it. 

So:
Is expect the solution?
Is there a guide/howto/tutorial you can link to?
Is there a better solution?

Hope that someone know what to do.

\asbjornn

---

### Post by cdtech on 2008-05-20
I have my /etc/sshd_config set with "TCPKeepAlive yes", keeps the session alive.

See ssh_config man page:
you can use the command line option -o TCPKeepAlive, ServerAliveInterval, ServerAliveCountMax

---

### Post by asbjornn on 2008-05-25
Thanks, cdtech. THis appears to have solved the problem.

\asbjornn

---

### Post by cdtech on 2008-05-25
cool, glad you got it working.

Good luck.......

---

