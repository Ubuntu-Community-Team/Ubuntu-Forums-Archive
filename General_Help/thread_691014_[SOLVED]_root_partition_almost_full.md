---
title: "[SOLVED] root partition almost full"
date: 2008-02-08
forum: General Help
---

### Post by goodfella on 2008-02-08
For some reason my root partition is full, but the output of 
```

du -xch --max-depth=1

```
is
> 
48K     ./lost+found
257M    ./var
4.0K    ./home
69K     ./media
19M     ./etc
4.9M    ./bin
8.2M    ./boot
0       ./dev
4.0K    ./initrd
92M     ./lib
4.0K    ./mnt
1.1G    ./opt
0       ./proc
5.3M    ./root
6.4M    ./sbin
4.0K    ./srv
0       ./sys
140K    ./tmp
3.1G    ./usr
4.6G    .
4.6G    total


I don't understand how this could be.  Here is the output of df
> 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5             10080488   8916140    652280  94% /


Any help please.

---

### Post by eggdeng on 2008-02-08
> 4.0K ./home
can hardly be right, can it? cd into your /home dir and run the command again.

---

### Post by chrisccoulson on 2008-02-08
> **eggdeng said:**
> can hardly be right, can it? cd into your /home dir and run the command again.

That will be because they have /home on a separate partition, and they ran du with the 'x' option, so it doesn't cross filesystem boundaries.

---

### Post by nemilar on 2008-02-08
If I'm understanding you, you're saying that the output of df isn't matching up with the output of du (one says 4+G while the other says 8).  This can happen if you've deleted a file, but a program is still keeping it open; du will register the deleted files as free space, but df will think it's still used.

You might try rebooting, and see if that helps the two of them match up.

---

### Post by nemilar on 2008-02-08
That 8) was not supposed to be an emoticon.  It was supposed to be 8G) as in 8 gigs, close-paren.

---

### Post by goodfella on 2008-02-09
After thinking about what could be the problem, I figured out that when my external drive was not mounted, the backups would be written to the directory where my external backup was to be mounted on.  When I ran du, my external backup drive was mounted thus hiding the files that were in the directory it was mounted on.  So basically I had two large files in my /media/ext-backup directory.  Once I deleted those all was back to normal.  Thanks for your posts.

---

