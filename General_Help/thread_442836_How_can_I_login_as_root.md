---
title: "How can I login as root?"
date: 2007-05-13
forum: General Help
---

### Post by anhkiet on 2007-05-13
Hi everyone, I have just downloaded Ubuntu Server version on Ubuntu website. when I install  it, it just required username and password (not root). So I can't login as root when installing finish.How  can I login as root?

---

### Post by rmfought on 2007-05-13
You can't - you have to login using your standard username - then you can do "sudo su" to get root access.

---

### Post by Wim Sturkenboom on 2007-05-14
You can if you enable the account by setting a password.
```
sudo passwd root
```

---

### Post by aysiu on 2007-05-14
You don't need to log in as root. Read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

