---
title: "Permissions"
date: 2007-06-11
forum: General Help
---

### Post by Programmerfromthehood on 2007-06-11
Okay so I have a volume mounted on my desktop in Ubuntu, when I want to unmount it, I have to go to my root account to do it because it say my admin account does not have to permissions, so how do I set in my root account so the my admin account can unmount this volume?

Thanks in advance.

---

### Post by carcioni on 2007-06-11
I assume 'sudo umount <device path>' doesn't work for you?

If you want to avoid using sudo, you could add your login user to the 'admin', or 'root' group but
that kind of defeats the purpose of sudo.

Cheers
C

---

### Post by Programmerfromthehood on 2007-06-11
> **carcioni said:**
> I assume 'sudo umount <device path>' doesn't work for you?

If you want to avoid using sudo, you could add your login user to the 'admin', or 'root' group but
that kind of defeats the purpose of sudo.

Cheers
COh crap, I forgot about that command in sudo, thanks. It does work for me.

---

