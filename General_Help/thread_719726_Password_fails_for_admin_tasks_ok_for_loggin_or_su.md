---
title: "Password fails for admin tasks ok for loggin or su"
date: 2008-03-09
forum: General Help
---

### Post by gillisboy on 2008-03-09
Hye everybody,
I already saw some posts about this subject but all what I tried had no effect. I've changed the root password and this one is always accepted when I login or when I enter the su command in a shell console. But when I want to click on an administrative job icon (ex : icon   network - Manual configuration), The box "Enter your password to perform administrative task" appears and when I enter my password, the same window comes back again with "Incorrect password...try again."

If someone has a idea, she would be welcome.

                  Gillisboy

---

### Post by aysiu on 2008-03-09
Ubuntu uses *sudo*, not root. So when you launch an administrative password, it is asking for your user password, not the root password. In fact, there's no reason for you to have set a root password in the first place.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

