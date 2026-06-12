---
title: "[SOLVED] Confusions with permissions while mounting extra partitions"
date: 2007-01-26
forum: General Help
---

### Post by xand on 2007-01-26
I've mounted a ntfs partition with the ntfs-3g driver and it worked just fine allowing any user to r/w the partition. However my goal was making it "full-access"  for me and not writable for any other user on the machine. My user named "xand" was created during install time. Then i created this "normaluser" account with the GUI user/group configurator of GNOME. 
Some info on them:
```

xand@xand-desktop:~$ id xand
uid=1000(xand) gid=1000(xand) grupos=1000(xand),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin)

```

```

id normaluser
uid=1001(normaluser) gid=1001(normaluser) grupos=1001(normaluser)

```

I tried putting my uid and gid on fstab and setting umask, and still with this code below normaluser can write on the partition:
```

/dev/sdb1       /media/ntfs     ntfs-3g owner,uid=1000,gid=1000,umask=0022,locale=pt_BR.utf8    0       0

```

This is what i get after mouting it:
```

 xand@xand-desktop:~$ ls -la /media/ntfs/
total 64
drwxr-xr-x 1 xand xand  4096 2007-01-25 14:01 .
drwxr-xr-x 8 root root  4096 2007-01-24 19:37 ..
-rwxr-xr-x 1 xand xand    42 2007-01-26 16:43 blah
-rwxr-xr-x 1 xand xand    40 2007-01-26 16:43 blah~
drwxr-xr-x 1 xand xand  4096 2007-01-16 10:55 Desktop
drwxr-xr-x 1 xand xand  4096 2007-01-16 10:57 filmes
drwxr-xr-x 1 xand xand  8192 2007-01-22 14:57 Meus documentos 2
drwxr-xr-x 1 xand xand  4096 2007-01-16 11:10 Minhas Imagens
drwxr-xr-x 1 xand xand 32768 2007-01-16 11:30 mp3
drwxr-xr-x 1 xand xand     0 2007-01-16 10:36 MSOCache
-rwxr-xr-x 1 xand xand     8 2007-01-26 13:47 novo arquivo.txt~
drwxr-xr-x 1 xand xand     0 2007-01-16 00:54 RECYCLER
drwxr-xr-x 1 xand xand  4096 2007-01-16 03:35 System Volume Information
drwxr-xr-x 1 xand xand     0 2007-01-26 12:15 .Trash-normaluser
drwxr-xr-x 1 xand xand     0 2007-01-26 14:06 .Trash-xand

```

The only way i could deny "normaluser" editing the partition was setting umask a value like "0222", which denies me either.

I'm running Ubuntu 6.10 , and ntfs-3g package version is 20060920-0ubuntu2.

---

### Post by geekgod on 2007-01-26
try 0772

---

### Post by xand on 2007-01-26
Thanks for your reply geekgod. Unfortunately it didn't work, neither me nor "normaluser" could edit files. As far as i know umask's way of thinking is sort of the opposite of chmod. So when i give fstab a "umask=0772", i'm denying the owner and owner's group any privileges over the files, and allowing other users write access.

This is what i get after "umask=0772"
```

xand@xand-desktop:~$ ls -la /media/ntfs/
total 64
d------r-x 1 xand xand  4096 2007-01-25 14:01 .
drwxr-xr-x 8 root root  4096 2007-01-24 19:37 ..
-------r-x 1 xand xand    40 2007-01-26 16:43 blah~
-------r-x 1 xand xand     0 2007-01-26 18:57 bleh
d------r-x 1 xand xand  4096 2007-01-16 10:55 Desktop
d------r-x 1 xand xand  4096 2007-01-16 10:57 filmes
d------r-x 1 xand xand  8192 2007-01-22 14:57 Meus documentos 2
d------r-x 1 xand xand  4096 2007-01-16 11:10 Minhas Imagens
d------r-x 1 xand xand 32768 2007-01-16 11:30 mp3
d------r-x 1 xand xand     0 2007-01-16 10:36 MSOCache
-------r-x 1 xand xand     8 2007-01-26 13:47 novo arquivo.txt~
d------r-x 1 xand xand     0 2007-01-16 00:54 RECYCLER
d------r-x 1 xand xand  4096 2007-01-16 03:35 System Volume Information
d------r-x 1 xand xand     0 2007-01-26 12:15 .Trash-normaluser
d------r-x 1 xand xand     0 2007-01-26 14:06 .Trash-xand

```

---

### Post by xand on 2007-02-08
Problem solved on the ntfs-3g Forums. Follow the link:
[http://forum.ntfs-3g.org/viewtopic.php?p=776#776](http://forum.ntfs-3g.org/viewtopic.php?p=776#776)

---

