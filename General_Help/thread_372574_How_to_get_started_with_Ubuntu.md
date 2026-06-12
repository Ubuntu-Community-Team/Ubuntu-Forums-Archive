---
title: "How to get started with Ubuntu?"
date: 2007-02-28
forum: General Help
---

### Post by Kayode on 2007-02-28
Dear Ubuntu User,

I have just installed Ubuntu version 5.10.  After it has booted, on the MS-Dos screen it asks me for my username and password, which I typed correctly. After I press 'enter' the message below appears:

kayode@ubuntu:~s

what are my suppose to do to get to the Ubuntu desktop interface?
Do i need to enter any command?

Please help!

Thanks

Kayode

---

### Post by taurus on 2007-02-28
What happens when you type this at that prompt?

```
startx
```

---

### Post by Falcorian on 2007-02-28
Your xwindows system isn't loading then?

Try:

```
startx
```

However, I don't know 5.10, so I can't be sure what's going on. ;)

---

### Post by Kayode on 2007-02-28
I typed the command : startx

but it displays 'command not found'

Must the command be typed in any standard format?

I still need help, please.

---

### Post by aysiu on 2007-02-28
This should help:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by cookfromfrozen on 2007-02-28
5.10 is quite old now and you should probably try the latest version, 6.10, or Dapper, version 6.06.

Back to the problem though, you may have installed the "server" profile by mistake, which does not install a graphical environment and will mean you only get a terminal.

I'd boot the CD again and verify that you picked the install option rather than "install a server".

---

