---
title: "cannot login - says my user is incorrect"
date: 2007-03-22
forum: General Help
---

### Post by anarchoi on 2007-03-22
This is weird....

I try to open my computer this morning and i enter the SAME EXACT username and password like i always did, and it says my login is incorrect...

I really don't know how it happenned, i didn't touch anything...

Yes i'm sure my user/pass is correct
Yes i know it's case-sensitive

But since i cannot login, i can't do anything... How can I create a new user without having to login to enter the graphical interface?

---

### Post by taurus on 2007-03-22
Boot into recovery mode from GRUB menu and change the password for your account, assuming it's called anarchoi.

```
passwd anarchoi
```
Reboot and see if you can log in with the new password.

```
shutdown -r now
```

---

### Post by anarchoi on 2007-03-22
Thanks!

this forum is wonderful :)

---

