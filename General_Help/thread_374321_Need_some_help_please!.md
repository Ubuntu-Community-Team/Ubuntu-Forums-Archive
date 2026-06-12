---
title: "Need some help please!"
date: 2007-03-02
forum: General Help
---

### Post by dark_diablo_01 on 2007-03-02
I can't access any of the administration items and there is only one account on my ubuntu pc which is under root. When it is "suppose" to launch the password promp all it does is say, "Starting Administrative application." then dissappears after about a minute.

I am also unable to sudo, also this is what I got when I tried to start dcopserver:

```

dillyn@Diablo OS:~$ dcopserver
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!


```

Any suggestions?

---

### Post by scrooge_74 on 2007-03-02
Did you tried doing it from a terminal?

there you use gksudo and the name of the application, that way you may be able to see any error messages

---

