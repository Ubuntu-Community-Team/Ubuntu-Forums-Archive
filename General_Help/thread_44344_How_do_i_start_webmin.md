---
title: "How do i start webmin?"
date: 2005-06-25
forum: General Help
---

### Post by Dave_is_sexy on 2005-06-25
there's no gnome menu entry and webmin as a command doesn't do anything. Anyone know the command? 

Thanks

---

### Post by cwaldbieser on 2005-06-25
It is actually a web page.  Try:

[http://localhost:10000](http://localhost:10000), or [https://localhost:10000](https://localhost:10000)

There is actually a somewhat smallish man page that explains this if you forget the port number (which I often do).

```
$ man webmin
```

Also, if you want to do any kind of administration with webmin, you will probably have to activate your root account, at least temporarily.  Then you can log in as root, give some other user account permission to use the various webmin tools you want to use, and deactivate the root account.

---

### Post by kastorff on 2005-06-25
IME, if the root account isn't active when you install webmin, it will *never* work in Ubuntu. You won't be able to log into webmin.

---

### Post by beatyou on 2005-07-07
[QUOTE=kastorff]IME, if the root account isn't active when you install webmin, it will *never* work in Ubuntu. You won't be able to log into webmin.[/QUOTE]
 in /etc/webmin/miniserv.users you can enable the account you use to login to ubuntu by putting

youraccount:* underneat the root entry.

---

