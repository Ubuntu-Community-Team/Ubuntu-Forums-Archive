---
title: "[SOLVED] Huge Problem"
date: 2008-05-16
forum: General Help
---

### Post by dozersmasher on 2008-05-16
I'm gonna guess that I wasn't supposed to remove the folders /tmp and /var/tmp, because now I'm in failsafe terminal wondering why nothing will start. I can't even start Metacity! does anyone know how to fix this kind of system crash?

---

### Post by da chicken on 2008-05-16
Once you log in at the console, you'll need to recreate the directory /tmp and then mark it with the temp sticky bit:

$ sudo mkdir /tmp
$ sudo chmod 1777 /tmp

You can recreate /var/tmp with the same commands.

An ls -l should look like this:
$ ls -ld /tmp
drwxrwxrwt  15 root root  4096 2008-05-16 18:33 tmp

---

### Post by dozersmasher on 2008-05-16
Thanks, It worked perfectly, and thanks for getting such a fast reply to me.:)

---

