---
title: "sudo or su-? why?"
date: 2007-05-16
forum: General Help
---

### Post by neoflight on 2007-05-16
friends,

could you please remind me again why sudo is better than su ?
i can do whatever i want with sudo in ubuntu. then why is root in ubuntu?

thanks

---

### Post by vtel57 on 2007-05-16
Read all about it [HERE](https://help.ubuntu.com/community/RootSudo).

---

### Post by aysiu on 2007-05-16
Ubuntu's sudo invokes root temporarily. If you don't have root, you can't have sudo. Having root exist as an account is not the same as logging into the root account.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by briealeida on 2007-05-16
Another aspect of it I love is it prevents a user from inadvertently making changes that cause fatal errors. It's kind of a protection against yourself (a positive implementation of that theory, anyway).

---

### Post by Death_Sargent on 2007-05-16
Basically if you use SU you are logging in as root meaning your open to attacks that need root acess.

If you use sudo you use root power. this way hackers can't take advantage of an actuall root sesion

---

