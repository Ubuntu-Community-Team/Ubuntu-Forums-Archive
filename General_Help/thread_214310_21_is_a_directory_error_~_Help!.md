---
title: "21 is a directory error ~ Help!"
date: 2006-07-12
forum: General Help
---

### Post by taekwondodogoof on 2006-07-12
I'm getting this same error over and over in a lot of apps. When doing a update for ubuntu, it crashes and when I highlight the little star Icon it tells me an error "Error: Opening the cache (E:Read error - read (21 is a directory))    then in terminal when getting apts manually I get 

```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6
Reading package lists... Done
E: Read error - read (21 Is a directory)

```

Any help on this?

---

### Post by taekwondodogoof on 2006-07-17
Anyone? I can't update or do barely anything with this error!

---

### Post by Ramses de Norre on 2006-07-17
I have no idea what this means but the output of ls -lA /etc/apt/ could maybe reveal some info..

---

### Post by taekwondodogoof on 2006-07-18
Hmmm... I see nothing that has to do with "21" when I run that, any other ideas? And thanks for the help :D

---

### Post by Ramses de Norre on 2006-07-18
Could you post the output? There doesn't necesarily have to be 21 in it, since the **I**t is capitalized I think 21 is an error code.. (but it's just an idea and I could be mistaking..)

---

### Post by taekwondodogoof on 2006-07-19
Ok, here's the output
```
jared@MeinKampf:~$ ls -lA /etc/apt/
total 108
-rw-r--r-- 1 root  root     30 2006-06-28 22:54 apt.conf
drwxr-xr-x 2 root  root   4096 2006-06-28 22:56 apt.conf.d
drwxr-xr-x 2 root  root   4096 2006-07-11 11:34 preferences
-rw------- 1 root  root      0 2006-05-30 19:51 secring.gpg
-rw-r--r-- 1 root  root   2724 2006-07-17 15:43 sources.list
-rw-r--r-- 1 root  root   2703 2006-07-11 11:26 sources.list~
-rw-r--r-- 1 root  root   1621 2006-07-10 20:55 sources.list_backup_200607102108-rw-r--r-- 1 root  root   1933 2006-06-30 13:11 sources.list_backup_200607171543drwxr-xr-x 2 root  root   4096 2006-06-28 23:34 sources.list.d
-rw-r--r-- 1 root  root   2855 2006-07-11 11:12 sources.list.save
-rw-r--r-- 1 jared jared  1621 2006-07-10 20:50 sources.list.txt
-rw------- 1 root  root   1200 2006-07-10 21:08 trustdb.gpg
-rw-r--r-- 1 root  root  30985 2006-07-10 21:08 trusted.gpg
-rw-r--r-- 1 root  root  30985 2006-07-10 21:08 trusted.gpg~
jared@MeinKampf:~$






```

---

### Post by mbeierl on 2006-07-21
This line:

> -rw-r--r-- 1 root  root   1621 2006-07-10 20:55 sources.list_backup_200607102108-rw-r--r-- 1 root  root   1933 2006-06-30 13:11 sources.list_backup_200607171543drwxr-xr-x 2 root  root   4096 2006-06-28 23:34 sources.list.d

looks suspicious, like you have a control character in your filename.  Try using 
```
ls -alb /etc/apt

```
to see if there is any binary characters in your filenames,

---

### Post by taekwondodogoof on 2006-07-23
Ok, thanks for the help again, here's what I get 
```
jared@MeinKampf:~$ ls -alb /etc/apt
total 120
drwxr-xr-x   5 root  root   4096 2006-07-17 15:46 .
drwxr-xr-x 124 root  root   8192 2006-07-23 00:19 ..
-rw-r--r--   1 root  root     30 2006-06-28 22:54 apt.conf
drwxr-xr-x   2 root  root   4096 2006-06-28 22:56 apt.conf.d
drwxr-xr-x   2 root  root   4096 2006-07-11 11:34 preferences
-rw-------   1 root  root      0 2006-05-30 19:51 secring.gpg
-rw-r--r--   1 root  root   2724 2006-07-17 15:43 sources.list
-rw-r--r--   1 root  root   2703 2006-07-11 11:26 sources.list~
-rw-r--r--   1 root  root   1621 2006-07-10 20:55 sources.list_backup_200607102108
-rw-r--r--   1 root  root   1933 2006-06-30 13:11 sources.list_backup_200607171543
drwxr-xr-x   2 root  root   4096 2006-06-28 23:34 sources.list.d
-rw-r--r--   1 root  root   2855 2006-07-11 11:12 sources.list.save
-rw-r--r--   1 jared jared  1621 2006-07-10 20:50 sources.list.txt
-rw-------   1 root  root   1200 2006-07-10 21:08 trustdb.gpg
-rw-r--r--   1 root  root  30985 2006-07-10 21:08 trusted.gpg
-rw-r--r--   1 root  root  30985 2006-07-10 21:08 trusted.gpg~
jared@MeinKampf:~$

```

---

### Post by taekwondodogoof on 2006-07-23
Quick bump =D

---

### Post by mbeierl on 2006-07-24
Hmmm.  That didn't seem to uncover much.

Just for giggles, can you delete (or move to another location) the sources.list_backup_* files?

I know their presence shouldn't affect anything, but we're grasping at straws here.

---

