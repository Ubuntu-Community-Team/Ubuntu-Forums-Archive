---
title: "Login with no password"
date: 2008-01-01
forum: General Help
---

### Post by dkonrad on 2008-01-01
My computer is shared by all members of our family. I would like my five year old daughter to be able to login without a password. How can I do this, without opening any gaping security holes? I consider physical access to the keyboard and mouse to be adequate.

Thanks
dk

---

### Post by pietjanjaap on 2008-01-01
With no password you should not do, this is unsafe.

But you can do automatic login, then you are stil safe.

---

### Post by shad0w_walker on 2008-01-01
[http://ubuntuforums.org/showthread.php?t=513820&highlight=guest+account](http://ubuntuforums.org/showthread.php?t=513820&highlight=guest+account)  

That thread should give you basically what you need, just need to apply the process to the account you want.

---

### Post by nutz on 2008-01-01
System>Administration>Login Window

In there you can set it to log someone in when the PC boots up and not prompt for a password. In this way if it gets logged out you can simply restart the computer and it will log that account in again. Hope that is what you are looking for...

---

### Post by shad0w_walker on 2008-01-01
> **pietjanjaap said:**
> With no password you should not do, this is unsafe.

But you can do automatic login, then you are stil safe.

This assumes that he will be using an admin capable account for the kid. Non admin account without sudo access and there is no real harm to be done.

---

### Post by ~LoKe on 2008-01-01
> **nutz said:**
> System>Administration>Login Window

In there you can set it to log someone in when the PC boots up and not prompt for a password. In this way if it gets logged out you can simply restart the computer and it will log that account in again. Hope that is what you are looking for...

This is the only viable way to do what you're after without compromising your system.

---

### Post by shad0w_walker on 2008-01-01
I don't see how not having a password on an account (Assuming its unprivileged) would actually compromise your systems security. As long as the account doesn't have rights to do anything that can damage the system (Remove them from sudoer list) I can't see any problem.

---

### Post by dkonrad on 2008-01-01
Can those of you who say I will be compromising my system provide a few more details? Can I configure her account so it will ONLY allow physical access? i.e. not access via the network? And if so, what are the risks?

Thanks
dk

---

### Post by dkonrad on 2008-01-01
Unfortunately,  this computer is shared. Other users need to be able to sign on (with a password).

---

