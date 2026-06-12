---
title: "how do i use command line to test open ports?"
date: 2007-08-01
forum: General Help
---

### Post by Hawk__0 on 2007-08-01
is there a command line program or something that i can use to test if ports are open? my dlink router is sometimes kinda hokey and well.. my torrent speeds are slow and i think my routers not allowing that port (even though its set to)

---

### Post by splintercellguy on 2007-08-01
If you want to test outside connectivity I suggest ShieldsUp!: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) Ignore the FUD on the pages.

---

### Post by Hawk__0 on 2007-08-01
i wanna check port 32659, but i dont see how i can check that with this site

---

### Post by Shib on 2007-08-01
$ telnet host port

if the screen goes blank (or a welcome message)... you have yourself a connection. otherwise it'll say connect refused.

you may need to apt-get install telnet.

---

