---
title: "Cannot Login after deleting /tmp"
date: 2013-01-21
forum: General Help
---

### Post by weissnich on 2013-01-21
hi,

I carelessly deleted the /tmp directory with rm -R tmp after getting the message "The disk drive for /tmp is not ready" on boot.
Now I cannot login with my user, every time i enter my password, I have to redo this again with no effect,
can anybody help?

---

### Post by SeijiSensei on 2013-01-21
Boot into recovery mode and choose "root shell" from the menu.  Now run these commands:

```

mount -o remount,rw /
mkdir /tmp
chmod 1777 /tmp
reboot

```

Note that there is no space after the comma.  You should now have a /tmp directory with the proper permissions

```
drwxrwxrwt  13 root root     4096 Jan 21 10:17 tmp
```

---

