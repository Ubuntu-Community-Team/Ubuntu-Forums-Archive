---
title: "GDM login with no password"
date: 2008-05-02
forum: General Help
---

### Post by marcolinux on 2008-05-02
I was trying to add this trick to login without using a password for certain users (kids...). 

```

sudo nano /etc/pam.d/gdm

# start login without password
auth sufficient pam_listfile.so item=user sense=allow file=/etc/gdm/nopassusers.txt onerr=fail
# end


```

(also adding /gdm/password file...)

It works in 7.04, 7.10 but in 8.04 it doesn't work and also, when i try to exit from gnome, desktop hangs for seconds.

any ideas?

thanks in advance and sorry for my rough english!

bb,
marco

ps: it seems [someone else]("http://backports.ubuntuforums.com/showthread.php?t=123116") is in trouble :-D

---

### Post by PinkFloyd102489 on 2008-05-02
Try this out.

[http://ubuntuforums.org/showthread.php?t=513820&highlight=shadow](http://ubuntuforums.org/showthread.php?t=513820&highlight=shadow)

---

