---
title: "root password for recovery mode"
date: 2008-05-04
forum: General Help
---

### Post by jesse c on 2008-05-04
I recently had a boot problem that i thought might be fixed by booting into recovery mode,but recovery boot starts its terminal page stuff and then it stops at some point and asks for my root password to continue ,and i dont remember my root password or even having made one.I did manage to straighten out my problems another way but now that i can use my computer how do i find my root pass in case i need recovery in the future?I know root is a dangerous thing but should it be written down somewhere for situations like this?

---

### Post by ghost_ryder35 on 2008-05-04
[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by mali2297 on 2008-05-04
When I boot in recovery mode, I get a root terminal without having to enter a password. I think that's the default behavior.

Anyway, the root password should be the same as the user password that you set during installation.

---

### Post by ghost_ryder35 on 2008-05-04
> **mali2297 said:**
> When I boot in recovery mode, I get a root terminal without having to enter a password. I think that's the default behavior.
 
Anyway, the root password should be the same as the user password that you set during installation.ubuntu does not set up a password for the root account during installation.  So unless he has enabled a password for it (post installtation) then the root account should not have a password.  However the link I provided will allow him to reset the password if any is set.

---

### Post by mali2297 on 2008-05-04
> **ghost_ryder35 said:**
> ubuntu does not set up a password for the root account during installation.  So unless he has enabled a password for it (post installtation) then the root account should not have a password.  However the link I provided will allow him to reset the password if any is set.

That makes sense. Thanks for the clarification.

---

### Post by ghost_ryder35 on 2008-05-04
no probs.  I get confused since I use Fedora at work and Ubuntu at home.  Fedora does not work well with Sudo, and they do not add the account created in the install to the sudoers file.  so in fedora i'm always using a root terminal by
```

su -

```
and in ubuntu i just always
```

sudo whatever command 

```

---

