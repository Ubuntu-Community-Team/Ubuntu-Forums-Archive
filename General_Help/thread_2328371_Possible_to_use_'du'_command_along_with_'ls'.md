---
title: "Possible to use 'du' command along with 'ls'?"
date: 2016-06-20
forum: General Help
---

### Post by peter1897 on 2016-06-20
Is it possible  to use du command along with ls, so i can get better information what are folders and what are files, and info about ownership and permissions? Something like ls usage in Find command: find ~/ -ls

Also, in this listing i see files with kilobytes size in front of files with megabytes size. Why is that? I assume 'K' stands for kilobytes and 'M' stands for megabytes:

```
max@ubuntu:/var/cache$ sudo du -sh * | sort -nr
93M     apt-xapian-index
50M     apt
32K     fontconfig
20K     ldconfig
8.0K    dbconfig-common
8.0K    apache2
4.9M    debconf
4.0K    pppconfig
4.0K    apparmor
1.3M    man
```

---

### Post by steeldriver on 2016-06-20
The 'h' in 

```

du -sh

```

stands for 'human readable' - ls also has that flag, so for example you could do

```

ls -sh

```
(with **size**, **human readable**) or

```

ls -lh

```

(**long** listing, **human readable** file sizes)

---

### Post by peter1897 on 2016-06-20
Yes, but for some reason ls -lh doesn't display the correct size of the directories for me:
```
max@ubuntu:/var/cache$ ls -lh
total 40K
drwxr-xr-x  3 root root 4.0K Dec 31 17:24 apache2
drwxr-xr-x  2 root root 4.0K May  1  2015 apparmor
drwxr-xr-x  3 root root 4.0K Jun 14 16:57 apt
drwxr-xr-x  3 root root 4.0K Jan  1 06:52 apt-xapian-index
drwxr-xr-x  3 root root 4.0K Dec 31 22:01 dbconfig-common
drwxr-xr-x  2 root root 4.0K Mar 16 03:01 debconf
drwxr-xr-x  2 root root 4.0K Mar 16 03:01 fontconfig
drwx------  2 root root 4.0K May 22 14:51 ldconfig
drwxr-sr-x 38 man  root 4.0K Jun 14 06:42 man
drwxr-xr-x  2 root root 4.0K Mar  7  2013 pppconfig
```

And this is the same directory using the du command:
```
max@ubuntu:/var/cache$ sudo du -sh * | sort -nr
93M     apt-xapian-index
50M     apt
32K     fontconfig
20K     ldconfig
8.0K    dbconfig-common
8.0K    apache2
4.9M    debconf
4.0K    pppconfig
4.0K    apparmor
1.3M    man
```

---

### Post by steeldriver on 2016-06-20
It is the correct size for the directories - but not for their contents ;)

If the latter is what you need, then du is the right command afaik. If you want it recusively, then you can exec du from find e.g.

```

find . -type d -exec du -h {} +

```

---

### Post by peter1897 on 2016-06-20
Thanks, it works. I tried these commands:
```
find ~/ -type d -exec du -h {} + | sort -nr
find ~/ -type f -exec du -h {} + | sort -nr
```

The first list only the directories sizes and the second only the files sizes, but what command to use to list directory and files in one listing? Also, what the '{}' and '+' signs mean?

---

