---
title: "[SOLVED] root password"
date: 2007-11-03
forum: General Help
---

### Post by jiggz88 on 2007-11-03
I need to access the root account inside of the wubi install. I was wondering what the default root password is because the standard user password wont work. Thankyou

---

### Post by aysiu on 2007-11-03
You don't log into root directly in Ubuntu.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jiggz88 on 2007-11-03
no i need it for su. i dont use sudo due to need of doing it in every command if you switch constantly between multiple terminals.

---

### Post by ruibernardo on 2007-11-03
jiggz88, read the end of the document that aysiu pointed. It talks about "sudo -i". I think that will do what you want whithout creating a root password. Try it.

---

### Post by jiggz88 on 2007-11-17
Thanks I missed that part when looking over the document. Thank you for your help.

---

