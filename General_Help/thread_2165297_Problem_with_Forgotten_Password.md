---
title: "Problem with Forgotten Password"
date: 2013-08-04
forum: General Help
---

### Post by eliseo_gomez on 2013-08-04
hi i need  help with my pc i lost my password i have ubuntu 12.4

---

### Post by howefield on 2013-08-04
Post moved to its own thread.

Don't be afraid to explain the issue in a bit more detail, help others to help you.

---

### Post by xeonix on 2013-08-04
@OP.

Please selet Ubuntu (Recovery Mode) at boot time and then select "Drop to root shell promt"
and reset your password by the command "passwd username_here"

---

### Post by steeldriver on 2013-08-04
There is a detailed walkthrough (with screenshots) here --> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by deadflowr on 2013-08-04
> **xeonix said:**
> @OP.

Please selet Ubuntu (Recovery Mode) at boot time and then select "Drop to root shell promt"
and reset your password by the command "passwd username_here"

Unfortunately, it's not as simple as just dropping into the root shell.
The recovery mode mounts the file system, as read only.
So it needs to be remounted.
The command needed to do so is in the link Steeldriver provided.

---

