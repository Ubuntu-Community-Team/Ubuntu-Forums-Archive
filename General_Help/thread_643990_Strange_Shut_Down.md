---
title: "Strange Shut Down"
date: 2007-12-18
forum: General Help
---

### Post by Goodkimchee on 2007-12-18
Hi.  I just reinstalled Ubuntu 7.10, and now when I power down, it goes to a 'Dos' (I know it's not dos, but I don't know what else to call it) screen with several statements about networking and then concludes with networking eth0 and eth1 off and then it just sits there.  

Having never seen this before with ubuntu, I'm curious as to where the normal shut down procedure has gone.  What's going on?  And how can I get the computer to shut down automatically?  FYI, I have a Compaq R3000, AMD64 3000+, 512MB Ram, 60G HD, Geforce4 4200, 15.1" screen, Broadcom wireless G.

Thanks in advance.

---

### Post by elliotjreed on 2007-12-18
Just sounds like it's not shutting down graphically, and it's getting stuck with the networking.

Try the command:

```
sudo shutdown -h now
```

and see what happens. If it works, crate a launcher (either on the desktop, or on the panel) with the command:

```
gksudo shutdown -h now
```

---

