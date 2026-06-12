---
title: "User Login Accepts Password, but Screen-lock does not?"
date: 2014-03-01
forum: General Help
---

### Post by orangeman555 on 2014-03-01
As title says, when I log in my password is accepted. The lock-out screen (after 5 minuts passes, you must put in a password) does not recognize the password.

Very strange! 

What causes this and how can it be fixed?

---

### Post by coldcritter64 on 2014-03-01
> **orangeman555 said:**
> As title says, when I log in my password is accepted. The lock-out screen (after 5 minuts passes, you must put in a password) does not recognize the password.

Very strange! 

What causes this and how can it be fixed?

Can you successfully log into a tty screen with ctrl + alt + f1 (ttys f1, f2, f3, f4, f5 or f6 are available) ? 

Try putting in your username and normal password for a bash login. This is to test authentication and your credentials elsewhere.

Try the command in terminal,
```
whoami
``` to check your login name. 
Authentication works against this name in some parts of the system, whereas your normal login name can vary slightly in some circumstances. One possible circumstance is when a user includes capital letters or special characters in their login name during initial installation.

---

### Post by orangeman555 on 2014-03-01
I'll check this and get back to you.

---

