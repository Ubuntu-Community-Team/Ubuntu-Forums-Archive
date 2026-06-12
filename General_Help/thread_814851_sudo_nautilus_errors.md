---
title: "sudo nautilus errors"
date: 2008-06-01
forum: General Help
---

### Post by aks2008 on 2008-06-01
Hi I am getting same errors as in this thread
[http://ubuntuforums.org/showthread.php?t=743502](http://ubuntuforums.org/showthread.php?t=743502)
But I can not post there as that forum is closed because it is hardy development forum. In that thread it says these are beta debugging errors and will be fixed by updates but I still get these errors.
 I understand from other thread that first half of error is because of uninstalled samba server and nothing to worry about but are the errors about
 "(nautilus:23149): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time"
 also because of same reason?

---

### Post by ibuclaw on 2008-06-01
It's possible.

Although, try switching to root and then running nautilus instead.
```

sudo -s
nautilus &

```

Regards
Iain

---

### Post by aks2008 on 2008-06-03
thanks tinivole
but it didn't work, it hangs while shutting down seahorse nautilus module.

 seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6869): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown

I had to close terminal window.

---

