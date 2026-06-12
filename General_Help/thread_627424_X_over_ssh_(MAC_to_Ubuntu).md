---
title: "X over ssh (MAC to Ubuntu)"
date: 2007-11-30
forum: General Help
---

### Post by reckless2k2 on 2007-11-30
I've seen the threads about setting up remote desktop on Ubuntu and using Chicken of the VNC on MAC to get this working. That's not what I'm looking to do. I'm looking for pure X over SSH in MAC to Ubuntu. 

In Linux I can flip to another console using Ctrl + Atl + F2. Then fire up an X session on that console using a command like xinit -- :1. So now I would have :0 running on F7 and :1 running on F9. 

My question is how can I do that on MAC? I have no idea how to flip to another terminal/console on MAC. Is it possible like you can do in Linux? If it is, then I can start an X session then ssh to the Ubuntu box and us startx to run X over SSH. 

Thanks.

---

### Post by navaburo on 2007-12-01
To allow X forwarding over SSH run:

```
ssh -X -lusername remotehost
```


As for the MAC VT switching, no idea.

---

### Post by reckless2k2 on 2007-12-01
yeah that was my first "simple" thought but you get :0 x server errors. i heard something about running xhost + first and then the normal ssh logins but i have yet to see if it'll work. sounds to me like i will only be able to possibly run some apps and not a desktop like you can do linux to linux.

---

