---
title: "GAIM Help"
date: 2007-04-27
forum: General Help
---

### Post by tnbyrnes on 2007-04-27
Hi there Ive just made the switch tonight to Ubuntu and I cant see why i didnt do it earlyier. My problem lies with GAIM. Seems like an excellent program as I use IM's alot. I have set up an account with my MSN accoutn and it seems to work. It connects just fine but as soon as it is signed in, I see my contacts list flash up and then it closes the program. has anyone else had issues with this or know what the problem might be? thanks alot.

---

### Post by tcpip4lyfe on 2007-04-27
Try this:

Open a terminal

```
Sudo apt-get update
```
```
sudo apt-get remove gaim
```
```
sudo apt-get install gaim
```

This will reinstall it as the newest version of gaim.  I suspect you are using the 6.0.3beta which has a MSN bug that crashes when you log in.   You want 6.0.31 or greater I believe.

---

