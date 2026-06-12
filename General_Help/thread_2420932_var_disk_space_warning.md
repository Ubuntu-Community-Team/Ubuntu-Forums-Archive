---
title: "var disk space warning"
date: 2019-06-13
forum: General Help
---

### Post by urungus on 2019-06-13
GUI users are reporting getting disk space warning "The volume "var" has only 196.0 MB disk space remaining" message box upon login.

Clicking "examine..." in the warning shows folder var listed as size 2.2GB and a red progress bar almost completely full.   Under that it shows red progress bar approx 80% full for "log" even though log's size is listed as 233.9 MB.  All other subfolders have green or empty progress bars.

However when I login via ssh, df command shows /var as using 9.4G of 19 G (plenty of free space):

```
$ df -h | sed -n '1p; /var/p'
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/podvmv4VG-varLV           19G  9.4G  7.9G  55% /var
```

And du command shows /var as taking up 12 G

```
$ sudo du -h /var --max-depth=1
16K     /var/lost+found
44K     /var/tmp
228M    /var/log
4.0K    /var/metrics
323M    /var/local
6.0M    /var/backups
40K     /var/snap
80K     /var/spool
139M    /var/cache
12M     /var/xdl
11G     /var/lib
4.0K    /var/opt
4.0K    /var/mail
2.2M    /var/crash
12G     /var
```

---

### Post by TheFu on 2019-06-13
How are the inodes?
df -i

---

### Post by urungus on 2019-06-13
> **TheFu said:**
> How are the inodes?
df -i

I am not an expert but it looks OK:

```
$ df -i | sed -n '1p; /var/p'
Filesystem                           Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/podvmv4VG-varLV         1220608  311223  909385   26% /var
```

---

### Post by deadflowr on 2019-06-13
What's in /var/lib?
Snap buildup maybe?

---

### Post by TheFu on 2019-06-13
Please show the complete output for the df commands.

And using code tags would be nice so things from the terminal line up correctly. For example:
```

df -hT 
df -i  
```
I suspect some important details are being hidden.

Thanks.

---

### Post by TheFu on 2019-06-13
deadflowr is onto something.

```
sudo apt autoremove
sudo apt autoclean
```
might do wonders.   apt could be hording old, unused, packages in /var/lib/apt|dpkg.  But without looking, no way to know.

Could have been a temporary file, used for processing in /var/tmp/ at the time of the error too. I don't know about the different versions of Ubuntu, but many Unix systems link /tmp/ and /var/tmp/

My specific df command above will also tell us about file systems.  Btrfs lies to both du and df, which causes no end of confusion.

---

