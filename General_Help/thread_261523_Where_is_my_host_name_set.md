---
title: "Where is my host name set?"
date: 2006-09-20
forum: General Help
---

### Post by Nick Wilson on 2006-09-20
hi all, 

im having dreadful trouble getting an email though to a list - postfix complains that the receiver doesnt like the unqualified hostname. 

it complains about the hostname 'nlaptop', and that is what i see with PS1="\u@\h:\W > " in my .bashrc but in /etc hosts i have this:

127.0.1.1 nlaptop.communicontent.com nlaptop.communicontent.com

and echo $HOSTNAME gives

nlaptop.communicontent.com

So, clearly im confused -- can anyone help me untangle this mess?

Many thx..

---

### Post by hw-tph on 2006-09-20
The hostname used by Postfix is set in /etc/postfix/main.cf using the configuration variable "myhostname".

So you would want to set it to something like this:
```
myhostname = nlaptop.communicontent.com
```

Reload Postfix and it should pick up the hostname as specified in main.cf.

Håkan

---

### Post by Nick Wilson on 2006-09-20
Great, thanks very much for the help!

It's working as expected now. 

Do you know where bash is getting the 'nlaptop' from?

---

### Post by skymt on 2006-09-20
> **Nick Wilson said:**
> Great, thanks very much for the help!

It's working as expected now. 

Do you know where bash is getting the 'nlaptop' from?

Probably /etc/hostname.

---

### Post by ayoli on 2006-09-21
> **Nick Wilson said:**
> Great, thanks very much for the help!

It's working as expected now. 

Do you know where bash is getting the 'nlaptop' from?

from /etc/hostname i guess

edit: oops, didnt see skymt post, morning is not my best time :)

---

