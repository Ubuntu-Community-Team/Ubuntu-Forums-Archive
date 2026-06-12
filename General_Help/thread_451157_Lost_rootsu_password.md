---
title: "Lost root/su password"
date: 2007-05-22
forum: General Help
---

### Post by Snorkel83 on 2007-05-22
Hi
I have installed ubuntu and I set all the password to the same, when i try to log in with su in terminal and the password I got this

torkel@torkel-laptop:~$ su
Password: 
su: Authentication failure
Sorry.

Can i reset my password anyway?

---

### Post by aysiu on 2007-05-22
There is no root account enabled.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want to reset your password, boot into recovery mode and type ```
passwd snorkel
reboot
```

---

