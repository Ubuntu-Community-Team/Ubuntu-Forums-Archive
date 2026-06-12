---
title: "forgot my user name and password"
date: 2008-07-06
forum: General Help
---

### Post by AznPat on 2008-07-06
i haven't use ubuntu in a while and i forgot my username and password is they're a way i can still log on..thanks guys

---

### Post by iaculallad on 2008-07-06
Boot Ubuntu using recovery mode.

The command below will display your user name:

```
ls -la /home
```

Assuming that it displays **Ibex**.

```
passwd Ibex
```

Then, reboot and log in as Ibex and use the password you typed earlier.

---

### Post by Rocket2DMn on 2008-07-06
If you have to reste the password, you can reboot into the recovery mode kernel, choose the command line interface, and run
```
passwd <username>
```
Then you can enter a new password for that user.

---

### Post by aysiu on 2008-07-06
If you have no idea what this recovery mode business is, check out this link:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

