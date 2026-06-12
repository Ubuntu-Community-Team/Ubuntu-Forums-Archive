---
title: "&quot;mount: cannot mount block device //athlon2400/shared read-only&quot;"
date: 2007-04-14
forum: General Help
---

### Post by yang on 2007-04-14
I can't access my share, on Windows XP:

```
$ sudo mkdir -p /mnt/home
$ sudo mount -t cifs -r //athlon2400/shared /mnt/home -o 'user=pawan,ip=123.456.78.9'
mount: cannot mount block device //athlon2400/shared read-only
$ sudo mount -t cifs //athlon2400/shared /mnt/home -o 'username=pawan,ip=123.456.78.9'
mount: block device //athlon2400/shared is write-protected, mounting read-only
mount: cannot mount block device //athlon2400/shared read-only
$ dmesg|tail -2
[18834496.420000]  CIFS VFS: Send error in SessSetup = -13
[18834496.552000]  CIFS VFS: cifs_mount failed w/return code = -13
```

I can access the share fine from my Windows and my FC5 boxen. I checked Windows Firewall too. Please help, thanks in advance.

---

### Post by yang on 2007-04-14
I just found a thread saying I have to install smbfs. This works!

---

