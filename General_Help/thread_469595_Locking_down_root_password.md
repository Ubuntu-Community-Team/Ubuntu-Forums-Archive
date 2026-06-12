---
title: "Locking down root password?"
date: 2007-06-10
forum: General Help
---

### Post by ThinkBuntu on 2007-06-10
I'm not pleased that my user account can freely edit the root password at any time, as if I were some super-super user. How can I lock down the root password, so that only root can change it? This is, after all, how things are supposed to be...

---

### Post by eentonig on 2007-06-10
> **ThinkBuntu said:**
> ...How can I lock down the root password, so that only root can change it? This is, after all, how things are supposed to be...

Read this
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

To answer your question. It is possible. I'm not going to tell you why, because I believe in the security this scheme provides. An it's one of the reason why I prefer Ubuntu over other distro's.

Only the first user has sudo rights by default. All the other users need to be added to the administrators group. (so if you want to disable your sudo access, remove yourself from the admin group).

And no, what you suggest is not as things are supposed to. It's one way of securing your stuff. This is yet another. Personally, my reason for preferring this way of working, is that users wont be tempted to default to the root login. And now, root-permission is only granted on the applications that require it, when they require it.

---

### Post by coffeecat on 2007-06-10
You might find this interesting reading too:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **eentonig said:**
> if you want to disable your sudo access, remove yourself from the admin group.

Er - you might want to make sure you've enabled the root account or created another account with administrative privileges first. :( :wink:

---

