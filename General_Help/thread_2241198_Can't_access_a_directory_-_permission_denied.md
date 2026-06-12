---
title: "Can't access a directory - permission denied"
date: 2014-08-24
forum: General Help
---

### Post by bphillips2 on 2014-08-24
I am trying to access my dir for bacula but keep getting the following error

```
[COLOR=#000000]brad@ubuntu:~$ cd /etc/bacula/
[/COLOR][COLOR=#000000]-bash: cd: /etc/bacula/: Permission denied[/COLOR]
```

I can't find out why it's doing this or how to fix it.

Here are my ownerships and permissions if it helps.

```
[COLOR=#000000]drwx------ 3 root root    4096 Jun 17 23:54 bacula[/COLOR]
```

Bonus question if anyone knows.  I'm currently backing up an Ubuntu 12.04 LTS server with bacula on a separate server.  It backs up the / directory.  If I build a new Ubuntu 12.04 LTS server could I just redirect the bacula settings to restore the old server to the new one and have an exact copy?

Thanks,

---

### Post by steeldriver on 2014-08-24
You need execute (x) permission on a directory in order to open it. Since only root has x permission, only root can cd to the dir.

You should be able to list the directory contents using

```

sudo ls /etc/bacula

```

however sudo won't work for the cd command because it's a shell builtin; instead you can enter an interactive root shell and then cd to the dir using

```

sudo -i
cd /etc/bacula

```

You can return to the non-root shell when you're done using

```

exit

```

---

