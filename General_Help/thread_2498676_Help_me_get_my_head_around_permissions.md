---
title: "Help me get my head around permissions"
date: 2024-06-23
forum: General Help
---

### Post by makem2 on 2024-06-23
I have a set of directories and files:

```

makem@makem-22:/media/makem/games-steam$ ls -la
total 36
drwxr-xr-x  6 makem makem  4096 Jun 23 12:25 .
drwxr-x---+ 6 root  root   4096 Jun 22 10:47 ..
drwxrwxr-x  3 makem makem  4096 Jun 23 12:28 jellyfin
drwx------  2 makem makem 16384 Aug  4  2023 lost+found
drwxrwxr-x  3 makem makem  4096 Jun 16 22:14 SteamLibrary_going
drwx------  5 makem makem  4096 Feb 14 19:51 .Trash-1000
makem@makem-22:~$

```

I want to allow the user jellyfin to access the jellyfin directory and it's contents as needed.

I cannot get the permissions correct.

---

### Post by makem2 on 2024-06-23
there is an ACL on /media/makem. The + sign


drwxr-x---+ 6 root root 4096 Jun 22 10:47 ..


sudo setfacl -b /media/makem


that will remove it
and then sudo chmod 755 /media/makem

---

