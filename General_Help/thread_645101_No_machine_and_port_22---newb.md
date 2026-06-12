---
title: "No machine and port 22---newb"
date: 2007-12-19
forum: General Help
---

### Post by localgod11 on 2007-12-19
I have installed No Machine on 2 of my home buntu PC's but i cant get them to connect when i attempt to connect I receive connection refused. when i run ssh localhost on the server side I get
"ssh: connect to host localhost port 22: Connection refused"

also netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::8888                 :::*                    LISTEN


ideas?

---

### Post by LaRoza on 2007-12-19
Is your router configured to forward that?

---

### Post by localgod11 on 2007-12-19
forgive my ignorance but  since this is all happening in my local network, should that matter?

---

