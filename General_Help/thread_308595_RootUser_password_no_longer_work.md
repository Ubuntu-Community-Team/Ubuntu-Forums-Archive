---
title: "Root/User password no longer work"
date: 2006-11-28
forum: General Help
---

### Post by fasajose on 2006-11-28
I created a new account(System->Administration->Users and Groups) and forgot to give it administrative privileges. I realized this after logging into the new account so I tried to log back into my old account but was not able to (password was not accepted). Also in the new account I am not able to use the sudo command. When ever i sudo ... it does nothing and goes to the new line. What did i do wrong or how can I fix it?

---

### Post by halfvolle melk on 2006-11-28
Boot into recovery mode and run
```
adduser <username> admin
```
That should add you to the sudoers. You can check this in the /etc/sudoers file.

---

### Post by fasajose on 2006-11-28
oops, did something stupid, please disregard my post.

---

