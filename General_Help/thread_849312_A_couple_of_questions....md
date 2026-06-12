---
title: "A couple of questions..."
date: 2008-07-04
forum: General Help
---

### Post by embryonic happy person on 2008-07-04
Hi,

I downloaded mercury messenger and it's not quite what I wanted after having a look and I want to remove it off the computer and I can't seem to find it in the add/remove area. Can someone tell me how I can find it and remove it from the system?

Also whenever I start up Evolution Mail for some reason it keeps asking me for something called a *keyring* and I need to put a password in. Is there a way to stop this coming up?

---

### Post by VMC on 2008-07-04
> **embryonic happy person said:**
> Hi,

I downloaded mercury messenger and it's not quite what I wanted after having a look and I want to remove it off the computer and I can't seem to find it in the add/remove area. Can someone tell me how I can find it and remove it from the system?

Also whenever I start up Evolution Mail for some reason it keeps asking me for something called a *keyring* and I need to put a password in. Is there a way to stop this coming up?

Try  "Applications > Add/Remove" , and then search for mercury.

That keyring is just another level of safety. You just type in once for your session. Since it was put in my thinking is , it's a small inconvenience for security.

---

### Post by embryonic happy person on 2008-07-04
> **VMC said:**
> Try  "Applications > Add/Remove" , and then search for mercury.

That keyring is just another level of safety. You just type in once for your session. Since it was put in my thinking is , it's a small inconvenience for security.

I did mention in my first post that I had tried to look for it in add/remove and didn't find it.

I did another search and it's not showing up.

---

### Post by VMC on 2008-07-04
From a Terminal type this:

```
sudo dpkg --get-selections mercury
```

Does it show up there?

---

