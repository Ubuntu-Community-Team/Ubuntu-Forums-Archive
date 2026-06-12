---
title: "CLI ? - cd to external drive?"
date: 2014-08-23
forum: General Help
---

### Post by Kurt_Alan on 2014-08-23
Using df I can confirm that my external drive is mounted: ```
 /dev/sdb1       1% /mnt 
``` 

When I try to access this drive I use: ```
 cd /dev/sdb1 
``` but I am informed that: ```
 bash: cd: /dev/sdb1: Not a directory 
```

Really? It's not a directory?

How do I access an external drive via CLI?

---

### Post by steeldriver on 2014-08-23
/dev/sdb1 is the raw *block device* - you need to use the directory to which it's mounted in the filesystem (which you can see from your df command - or by running the 'mount' command without arguments)

```

cd /mnt

```

---

### Post by ajgreeny on 2014-08-23
Depending on your version of Ubuntu it will be **cd /media/disk-name** or for the latest versions **cd /media/username/disk-name** on the assumption that the disk is automounted when you attach it.

---

### Post by Kurt_Alan on 2014-08-24
> **ajgreeny said:**
> Depending on your version of Ubuntu it will be **cd /media/disk-name** or for the latest versions **cd /media/username/disk-name** on the assumption that the disk is automounted when you attach it.

Your last suggestion did the trick. This output shows that I could check the drive--it is empty   ```
   santa@santahp:~$ cd /media/santa/fd04e913-5b47-44ab-b159-63edfbb20083/
santa@santahp:/media/santa/fd04e913-5b47-44ab-b159-63edfbb20083$ ls
lost+found
  
```

Thanks.

---

