---
title: "Default Permissions for /etc/ssh folder &amp; /etc/ssh/sshd_config file?"
date: 2013-08-02
forum: General Help
---

### Post by Chris of Arabia on 2013-08-02
Could someone tell me what the default folder/file permissions for the **/etc/ssh** folder & the **/etc/ssh/sshd_config** file are after first installation? Mr. Clumsy here has inadvertently set them to something else and would rather like to get back to the start point so he can try again...

Edit: Currently, they are:
[INDENT]
/etc/ssh = drwxr-xr-x (755)

and...

/etc/ssh/sshd_config = -rw-rw-rw- (666)[/INDENT]

---

### Post by steeldriver on 2013-08-02
AFAIK these are correct
```

$ ls -ld /etc/ssh/
drwxr-xr-x 2 root root 4096 Apr 22 18:06 /etc/ssh/
$
$ ls -l /etc/ssh/sshd_config
-rw-r--r-- 1 root root 2489 Jan 10  2013 /etc/ssh/sshd_config

```

---

### Post by Chris of Arabia on 2013-08-02
OK, thanks. It looks like it's just the config file I've got wrong then

---

### Post by CaptainMark on 2013-08-03
Not quite actually, /etc/ssh/sshd_config should have 644 permissions, its a system file after all so 666 would give average users write access which is a no-no for most setups. Nothing outside of your home folder should have permissions higher than -55, and most stuff inside your home folder too

---

