---
title: "/etc/init.d/rc: Permission denied"
date: 2008-06-28
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-06-28
I did something really stupid and changed the permissions of the whole etc/ directory! After I did that I got this error: ```
/etc/sudoers is mode 0666, should be 0440
``` so I did the following: ```
chmod -R 0440 /etc
``` and that sorted out that problem but now I got this error: ```
/etc/init.d/rc: Permission Denied
init: rc2 main process terminated with status 2
```

Please help me... I really don't want to re-install unless it means I won't lose all my installed packages and data...

---

### Post by Gunman1982 on 2008-06-28
Uhm first of all, don't reboot, do the 'chmod -R 755 /etc' first or you will leave your system severely crippled. Yes it means you have a big security hole but at least your system runs for now.

With the -R you went through all directories recursevely and with 440 you stripped all directories in /etc from the right being accessed by anyone. Means the system can't access the scripts there anymore.

I don't have an easy solution handy right now but I will look for one. Another solution would be to go through the files and change the permission one by one.

There is already another old thread about a similar problem [http://ubuntuforums.org/showthread.php?t=95484]("http://ubuntuforums.org/showthread.php?t=95484") I wouldn't recommend doing the method since some files in /etc still need to be executable and some not.

---

### Post by 4t0m1c_w07f on 2008-06-28
I already rebooted which stuffed it up even more... I am now booted into the live disc... Please can you give me step by step instructions...

---

### Post by conscious on 2008-06-28
You can reboot into the recovery mode and run the command suggested by Gunman1982.

---

### Post by 4t0m1c_w07f on 2008-06-28
Ok I did that and the output was ```
chmod: changing permissions of '*file name*': Read-only file system
```

---

### Post by 4t0m1c_w07f on 2008-06-28
Typed reboot and got the following:
```
init: rcs-sulogin main process (2666) killed by TERM signal 
exec: 12: /etc/init.d/rc: Permission denied
init: rc6 main process (2691) terminated with status 2
```

---

### Post by Gunman1982 on 2008-06-28
Boot the live cd, open a console and execute 'fdisk -l' that should give you an output like
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3681    29567601    7  HPFS/NTFS
/dev/hda2            3682        3749      498015   82  Linux swap / Solaris
/dev/hda3            3750        8783    40435605   83  Linux

```
the one of interest is the Linux partition on /dev/hda3 in my case, yours may differ of course. Then execute 'mkdir /mnt; mount /dev/hda3 /mnt && chmod -R 755 /mnt/etc'. After that you can reboot without livecd, at least I hope

---

