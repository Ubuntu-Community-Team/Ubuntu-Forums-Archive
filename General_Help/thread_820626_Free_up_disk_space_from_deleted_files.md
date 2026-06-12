---
title: "Free up disk space from deleted files"
date: 2008-06-06
forum: General Help
---

### Post by confuciusquinn on 2008-06-06
Hi, i deleted a file and it apparently didn't free up its used storage space. the command i used was this:

```
sudo rm error.log ; sudo touch error.log
```

The file was 4.5G on a 10G file system but i still have about 84% of the file system used. this is what happens when i do 'df'

```
#: df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  7.5G  1.5G  85% /
varrun                129M   44K  129M   1% /var/run
varlock               129M     0  129M   0% /var/lock
udev                  129M   16K  129M   1% /dev
devshm                129M     0  129M   0% /dev/shm
```

any ideas? 

also, here is the outputs when i deleted the log file:

```
#: ls -lh
total 4.5G
-rw-r--r-- 1 root root 4.5G 2008-06-06 16:05 error.log
#: sudo rm error.log ; sudo touch error.log 
#: ls -l
total 0
-rw-r--r-- 1 root root 0 2008-06-06 16:14 error.log

```

---

### Post by confuciusquinn on 2008-06-06
that may be a little confusing for people only looking at the 'code' sections, i did the df **after** i rm'd the log file.

---

### Post by bingoUV on 2008-06-06
If some application is using the file error.log, its space will not be freed up. It is likely the application that created it that is still using it. Close the application, or ask it to relinquish control on the file, for the space to get freed.

---

### Post by confuciusquinn on 2008-06-06
great, that worked. I just rebooted the box and it freed up the space. Also, for anyone curious, i think i could've used the 'fuser' command to figure out who was using it before i deleted it, which would've probably been a better.

---

