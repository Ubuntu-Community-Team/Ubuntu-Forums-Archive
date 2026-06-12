---
title: "How to run Gaim 2.0"
date: 2007-05-18
forum: General Help
---

### Post by lsutiger on 2007-05-18
I successfully installed Gaim 2.0 from source ( my first YAY!), but how do I run it? When I type gaim I get the 1.5 version.
Thanx in advance!

---

### Post by taurus on 2007-05-18
Maybe you installed the latest version in /usr/local/bin while the older version is in /usr/bin.  I bet /usr/bin is in your path before /usr/local/bin so when you just type in the name for it, it finds it in /usr/bin first and therefore, you get the older version.

So, you can try something like

```
/usr/local/bin/gaim
```

---

### Post by lsutiger on 2007-05-18
bash: /usr/local/bin/gaim: No such file or directory

I ran the ./configure, make and make install from my home/download/pidgin..../folder

---

### Post by taurus on 2007-05-18
You mean you only ran "make install" not "**sudo** make install"?

It could be called pidgin, not gaim with the latest version.

```
pidgin
```

---

### Post by lsutiger on 2007-05-18
Ok the run is called pidgin, but where is the jabber for Gtalk (google talk)?

---

### Post by lsutiger on 2007-05-18
I hve googled the heck out of this and nothing I hve come across has worked. I getting the following error when trying to connect gtalk in Pidgin (Gaim 2.0).
server requires TLS/SSL for login.
I am positive I have all of the settings correct.
Any idea?
PS - I can telnet to talk.google.com on port 5222

---

### Post by lsutiger on 2007-05-19
bump

---

### Post by lsutiger on 2007-05-23
bumpity, bumpity, bumpity, BUMP

---

