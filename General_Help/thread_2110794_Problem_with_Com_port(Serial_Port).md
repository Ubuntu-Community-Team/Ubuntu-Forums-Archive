---
title: "Problem with Com port(Serial Port)"
date: 2013-01-31
forum: General Help
---

### Post by Digvijay P on 2013-01-31
I followed all steps...
```
digupats@ubuntu:~$ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 Jan 31 11:26 /dev/ttyS0

digupats@ubuntu:~$ groups
digupats adm dialout cdrom plugdev lpadmin admin sambashare

digupats@ubuntu:~$ ln -s /dev/ttyS0 ~/.wine/dosdevices/com1
ln: failed to create symbolic link `/home/digupats/.wine/dosdevices/com1': File exists
```

Do the needful.What is the problem in creating symbolic link?

---

### Post by The Cog on 2013-01-31
Moved post to its own thread.

Referenced thread: [http://ubuntuforums.org/showthread.php?t=1664660](http://ubuntuforums.org/showthread.php?t=1664660)

> I followed all steps...
```
digupats@ubuntu:~$ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 Jan 31 11:26 /dev/ttyS0

digupats@ubuntu:~$ groups
digupats adm dialout cdrom plugdev lpadmin admin sambashare

digupats@ubuntu:~$ ln -s /dev/ttyS0 ~/.wine/dosdevices/com1
ln: failed to create symbolic link `/home/digupats/.wine/dosdevices/com1': File exists
```

Do the needful.What is the problem in creating symbolic link?
The problem is that the symbolic link already exists - it is **already** created. You can check that it points to the right place with this command:
```
ls -l ~/.wine/dosdevices/com1
```

---

