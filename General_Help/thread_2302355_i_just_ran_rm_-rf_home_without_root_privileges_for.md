---
title: "i just ran rm -rf /home without root privileges for about three seconds..."
date: 2015-11-09
forum: General Help
---

### Post by Mate_Timar on 2015-11-09
... so far i see no difference. I restarted my machine twice, and my desktop environment is still functioning. Everything seems to be fine. Do you have an idea how to restore the data I deleted?

Feel free to warn me if I posted this thread to a wrong place.

---

### Post by SeijiSensei on 2015-11-09
I'd guess some files in /home/username are missing.  Did you check there? If you don't have backups, they're lost.

---

### Post by Habitual on 2015-11-09
```
ls -ld /home
drwxr-xr-x 5 root root 4096 Aug 11 2015  1:32 PM /home
```

without sudo, nothing should have happened.

---

### Post by QIII on 2015-11-09
A couple of things to note:

The rm command doesn't send things to the trash can.  Once rm'ed, it's gone - unless you have some skill with forensics.

I usually mv things as backups first when working on files I want to get rid of.  Mistakes can easily be rectified.  When I'm satisfied things are good, I rm the backups.

---

### Post by jerome1232 on 2015-11-09
> **Habitual said:**
> ```
ls -ld /home
drwxr-xr-x 5 root root 4096 Aug 11 2015  1:32 PM /home
```

without sudo, nothing should have happened.

It's a recursive rm which means it will try to delete everything under /home as well, some of which presumably will be the user's personal files, in their user directory which is under /home.

If the op doesn't have a backup the only method I have used to recover some personal files such as documents and pictures  is photorec, it's worked great for me in the past but it's a messy recovery that you have to sort through and etc...

Hopefully you (the op) use the system backup tool (dejadup) to do backups. Use it to restore any missing files.

---

### Post by monkeybrain20122 on 2015-11-10
Out of curiosity, why did you do that??

---

### Post by howefield on 2015-11-10
> **Mate_Timar said:**
> ... so far i see no difference. I restarted my machine twice, and my desktop environment is still functioning....

Not sure I believe this, you would notice a difference immediately.

Are you telling us the whole story ?

---

### Post by Habitual on 2015-11-10
```
touch c9rocks && ls -al
total 8
drwxr-xr-x 2 vro  vro  4096 Nov 10 06:21 ./
drwxr-xr-x 3 root root 4096 Nov  3 09:39 ../
-rw-rw-r-- 1 vro  vro     0 Nov 10 06:21 c9rocks
vro@ubuntu:~$ touch c9rocks && ls -al && rm -fr /home
total 8
drwxr-xr-x 2 vro  vro  4096 Nov 10 06:21 ./
drwxr-xr-x 3 root root 4096 Nov  3 09:39 ../
-rw-rw-r-- 1 vro  vro     0 Nov 10 06:21 c9rocks
rm: cannot remove &#8216;/home/vro&#8217;: Permission denied
vro@ubuntu:~$ ls -al
total 8
drwxr-xr-x 2 vro  vro  4096 Nov 10 06:21 ./
drwxr-xr-x 3 root root 4096 Nov  3 09:39 ../
```

> **howefield said:**
> Are you telling us the whole story ?

I have to agree. Something is amiss.

---

