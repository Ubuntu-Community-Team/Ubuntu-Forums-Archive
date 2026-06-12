---
title: "Why the uninstall command is not recognized by Ubuntu?"
date: 2013-01-10
forum: General Help
---

### Post by ruwan2 on 2013-01-10
Hi,

I want to uninstall a software. When I enter:

sudo uninstall_CCSv5

It echoes:

sudo: uninstall_CCSv5: command not found

When I list the folder files, I notice that all the uninstall category files are in green, and there is a 'd' letter in the first column. Could you tell me how to run the uninstall command?

Thanks,

......
n2-MS-7696:/usr/local/CCSv5/ccsv5$ ls -list
total 6056
146379    4 drwxr-xr-x 11 root root    4096 Jan  9 18:14 eclipse
147660 1452 -rwxr-xr-x  1 root root 1485410 Jan  9 12:34 uninstall_CCSv5
407918    4 drwxr-xr-x  3 root root    4096 Jan  9 12:34 graphics
407665    4 drwxr-xr-x  4 root root    4096 Jan  9 12:34 doc
147658 1160 -rwxr-xr-x  1 root root 1187316 Jan  9 12:34 uninstall_dvt
275684    4 drwxr-xr-x 16 root root    4096 Jan  9 12:33 ccs_base_5.0.3.00028
147657 1140 -rwxr-xr-x  1 root root 1163458 Jan  9 12:33 uninstall_idecore

---

### Post by howefield on 2013-01-10
Try

```
sudo apt-get remove file
```

Where you substitute "file" with the name of the package you want to remove.

---

### Post by tartalo on 2013-01-10
Edit: Nevermind, my answer was wrong.

---

### Post by cliddell on 2013-01-10
> **ruwan2 said:**
> Hi,

I want to uninstall a software. When I enter:

sudo uninstall_CCSv5

It echoes:

sudo: uninstall_CCSv5: command not found

When I list the folder files, I notice that all the uninstall category files are in green, and there is a 'd' letter in the first column. Could you tell me how to run the uninstall command?


For security reasons, Unix type systems tend not to have the current directory in the search path, so you need to be explicit:

sudo ./uninstall_CCSv5



HTH,

Chris

---

### Post by ibjsb4 on 2013-01-10
[Removal commands]("https://help.ubuntu.com/community/AptGet/Howto#Removal_commands")

---

### Post by oldos2er on 2013-01-10
The "d" in the file list means that item is a directory.

It looks like uninstall_CCSv5 is a Windows app; did you install it with wine?

---

