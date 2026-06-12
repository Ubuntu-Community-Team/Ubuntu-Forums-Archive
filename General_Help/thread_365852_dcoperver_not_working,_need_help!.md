---
title: "dcoperver not working, need help!"
date: 2007-02-20
forum: General Help
---

### Post by dark_diablo_01 on 2007-02-20
I can't access any of the administration items and there is only one account on my ubuntu pc which is under root.  When it is "suppose" to launce the password promp all it does is say, "Starting Administrative application." then dissappears after about a minute.

I tried starting dcopserver and this is what i got:
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

### Post by dark_diablo_01 on 2007-02-22
Bump :(

---

### Post by raffytaffy on 2007-02-22
try removing your .ICEauthority  from home folder

sudo rm /.ICEauthority  and Xauthority if its there....reboot and hope it works.

---

### Post by dark_diablo_01 on 2007-02-22
That's another problem everytime I try to sudo I always get this:
 unable to lookup Diablo OS via gethostbyname()

---

### Post by dark_diablo_01 on 2007-02-22
Can someone seriously help?  I need to install Cedega and change some settings really bad.

---

### Post by dark_diablo_01 on 2007-02-22
Bump again... :(

---

