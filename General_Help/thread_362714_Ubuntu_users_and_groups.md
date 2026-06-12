---
title: "Ubuntu users and groups"
date: 2007-02-15
forum: General Help
---

### Post by stchman on 2007-02-15
Hello all I think I really hosed my Ubuntu installation.

I was messing around with users and such and now I cannot add or remove users.  The System --> Administration ---> Users and Groups is GONE.  How do I get it back?  Do I have to reinstall Ubuntu?

I am running Ubuntu 6.10.

Please help.

---

### Post by 3rdalbum on 2007-02-16
You may need to boot into recovery mode, by selecting its entry from GRUB.

When the desktop loads, go into the terminal and type:

```
users-admin
```

This will load the Users And Groups program and you'll be able to reverse the changes you made previously.

---

### Post by stchman on 2007-02-16
> **3rdalbum said:**
> You may need to boot into recovery mode, by selecting its entry from GRUB.

When the desktop loads, go into the terminal and type:

```
users-admin
```

This will load the Users And Groups program and you'll be able to reverse the changes you made previously.

I did that and entered the following in recovery mode:

sudo usermod -G admin <username>

It added the user to the admin group  and when i went back in the Users and Groups was there.

---

