---
title: "GAIM won't login"
date: 2007-03-18
forum: General Help
---

### Post by tjb891 on 2007-03-18
GAIM is hanging up on login and refuses to authenticate with the server and login. I can login with AIM Express but Gaim refuses to. Can anyone tell me how to debug this so I can provide more specific information?

auth host:login.oscar.aol.com

auth port: 5190

Encoding: ISO-8859-1

using aim proxy server box checked

---

### Post by tribble222 on 2007-03-18
you could start gaim from the terminal with the -d flag for debug info

gaim -d

---

### Post by tjb891 on 2007-03-18
The situation was resolved by me changing the port used. I don't know why but it worked so im good.

---

