---
title: "About pmount"
date: 2006-11-21
forum: General Help
---

### Post by satimis on 2006-11-21
Hi folks,

I have "pmount" running here.

$ which pmount```

/usr/bin/pmount
```

$ cat /etc/group | grep plugdev```

plugdev:x:1004:haldaemon,satimis
```


I want to mount the USB enclosure as User;

$ pmount /dev/sda1
$ ls -al /media/sda1/```

total 8
drwxr-xr-x 2 root root 4096 Nov 21 19:07 .
drwxr-xr-x 6 root root 4096 Nov 21 19:16 ..
-rw------- 1 root root    0 Nov 21 19:07 .created_by_pmount
```

The device is mounted as root

$ umount /dev/sda1
$ pmount -wAe /dev/sda1
$ ls -al /media/sda1/```

total 8
drwxr-xr-x 2 root root 4096 Nov 21 19:07 .
drwxr-xr-x 6 root root 4096 Nov 21 19:16 ..
-rw------- 1 root root    0 Nov 21 19:07 .created_by_pmount
```

also as root

$ cp Wallpaper_20061120.tar.bz2 /media/sda1/```

cp: cannot create regular file `/media/sda1/Wallpaper_20061120.tar.bz2': Permission denied

```

It works only if as root.

I have been playing around on /etc/pmount.allow

$ cat /etc/pmount.allow```

# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
satimis/user etc.

```

It did not help.  Any suggestion?  TIA

OR

$ su
Password:

# chmod -c 775 -R /media/sda1```

mode of `/media/sda1' changed to 0775 (rwxrwxr-x)
mode of `/media/sda1/.created_by_pmount' changed to 0775 (rwxrwxr-x)
```

# chown -c satimis:satimis -R /media/sda1```

changed ownership of `/media/sda1/.created_by_pmount' to satimis:satimis
changed ownership of `/media/sda1' to satimis:satimis
```

# exit
exit
$ cp Wallpaper_20061120.tar.bz2 /media/sda1/
$ ls -al /media/sda1/```

total 396
drwxrwxr-x 2 satimis satimis   4096 Nov 21 23:32 .
drwxr-xr-x 6 root    root      4096 Nov 21 19:16 ..
-rwxrwxr-x 1 satimis satimis      0 Nov 21 19:07 .created_by_pmount
-rw-r--r-- 1 satimis satimis 392570 Nov 21 23:32 Wallpaper_20061120.tar.bz2

```

Then it works.  However I must run both chown and chmod after each mounting.  Any glue?


B.R.
satimis

---

