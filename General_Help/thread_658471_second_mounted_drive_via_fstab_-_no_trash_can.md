---
title: "second mounted drive via fstab - no trash can?"
date: 2008-01-04
forum: General Help
---

### Post by shawnrgr on 2008-01-04
I'm able to get my second hard drive (ext3 200gig) mounted at boot. However I'm unable to get nautilus to move files to trash, it says its unable to and must delete permanently. I remember before my gusty install, I was able to do this without any problems. Possibly my fstab line, but I'm not sure. Anyone have any good ideas?

Here is the entry in my fstab:
```

# /dev/sdb1
  /dev/sdb1	/var/local/storage	ext3	user,auto	0	2

```

---

### Post by shawnrgr on 2008-01-04
I have to leave soon... therefore...a shameless bump :(

---

### Post by taurus on 2008-01-04
Do you have write permission to /var/local/storage?

Applications -> Accessories -> Terminal
```
ls -la /var/local/storage
```

---

### Post by shawnrgr on 2008-01-04
I created the .Trash-home as root and gave all permissions to homepc user (me) still same issue 
```

homepc@homepc-desktop:~$ ls -la /var/local/storage
total 104
drwxr-xr-x  6   1002 slocate  4096 2007-12-19 16:02 .
drwxrwsr-x  3 root   staff    4096 2007-10-16 11:54 ..
drwxrwxrwx 17 homepc homepc   4096 2008-01-04 18:37 drive2
drwx------  2 root   root    16384 2007-06-16 12:14 lost+found
drwxrwxrwx  2 homepc homepc  69632 2007-10-14 09:22 .Trash-home
drwx------  2 root   root     4096 2007-12-19 16:02 .Trash-root
```

---

### Post by taurus on 2008-01-04
> **shawnrgr said:**
> I created the .Trash-home as root and gave all permissions to homepc user (me) still same issue 
```

homepc@homepc-desktop:~$ ls -la /var/local/storage
total 104
drwxr-xr-x  6   1002 slocate  4096 2007-12-19 16:02 .
drwxrwsr-x  3 root   staff    4096 2007-10-16 11:54 ..
drwxrwxrwx 17 homepc homepc   4096 2008-01-04 18:37 drive2
drwx------  2 root   root    16384 2007-06-16 12:14 lost+found
drwxrwxrwx  2 homepc homepc  69632 2007-10-14 09:22 .Trash-home
drwx------  2 root   root     4096 2007-12-19 16:02 .Trash-root
```

But the only problem is you don't have permission to write to /var/local/storage.  So, if you want to write to /var/local/storage, you need to either change permissions for world or change the ownership of /var/log/storage from 1002 to your login name, homepc.

```
sudo chown homepc:homepc /var/local/storage
ls -la /var/local
```

---

### Post by shawnrgr on 2008-01-04
props! thank you so much!

---

