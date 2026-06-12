---
title: "ERROR on Package Manager"
date: 2008-03-04
forum: General Help
---

### Post by himalakas on 2008-03-04
Hi, wen I run the package Manager it gives an error which is -

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

How can I solve this problem, Please HELP.

---

### Post by Oldsoldier2003 on 2008-03-04
> **himalakas said:**
> Hi, wen I run the package Manager it gives an error which is -

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

How can I solve this problem, Please HELP.
in a terminal:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by himalakas on 2008-03-04
Tanx "Oldsoldier2003", I culd solve it. CU:lolflag:

---

### Post by leebra on 2008-03-05
im having the same problem but when i enter sudo dpkg --configure -a the terminal returns

dpkg: unable to access dpkg status area: Read-only file system

please help

---

### Post by kellemes on 2008-03-05
> **leebra said:**
> im having the same problem but when i enter sudo dpkg --configure -a the terminal returns

dpkg: unable to access dpkg status area: Read-only file system

please help

Are you sure you're doing..
```
sudo dpkg --configure -a
```

I don't understand why you would get this message since you have the correct privileges.

---

### Post by leebra on 2008-03-05
could this because of an error in the file system setup if so what do i need to look for i am a bit a new to this and this is my first ubuntu install

---

### Post by Oldsoldier2003 on 2008-03-05
> **leebra said:**
> could this because of an error in the file system setup if so what do i need to look for i am a bit a new to this and this is my first ubuntu install
make sure you are using a logon in the admin group, not a restricted user. sudo doesn't work on accounts that are not a member of the admin gorup. to see what group memberships you hold, open a terminal and type:

```
id
``` then hit enter. Please paster the entire result into a reply here so we can see for certain if you are a member of the group. It will help us in the way we approach your problem.

---

### Post by leebra on 2008-03-05
this is what i got for inputting < id >
uid=1000(leebra) gid=1000(leebra) groups=0(root) ,4(adm) ,20(dailout) ,21(fax) ,24cdrom) ,25(floppy) ,29(audio) ,30(dip) ,46(plugdev) ,104(scanner) ,106(fuse) ,108(lpadmin) ,110(admin) ,117(powerdev) ,1000(leebra)

---

### Post by Oldsoldier2003 on 2008-03-05
> **leebra said:**
> this is what i got for inputting < id >
uid=1000(leebra) gid=1000(leebra) groups=0(root) ,4(adm) ,20(dailout) ,21(fax) ,24cdrom) ,25(floppy) ,29(audio) ,30(dip) ,46(plugdev) ,104(scanner) ,106(fuse) ,108(lpadmin) ,110(admin) ,117(powerdev) ,1000(leebra)

ok please do this in a terminal:

```
cd /var/lib/dpkg/
ls -l
```
and paste the results so we can see your permissions

---

### Post by leebra on 2008-03-06
> **Oldsoldier2003 said:**
> ok please do this in a terminal:

```
cd /var/lib/dpkg/
ls -l
```
and paste the results so we can see your permissions

:/var/lib/dpkg$ ls -l
total 4544
drwxr-xr-x 2 root root    4096 2008-03-03 19:51 alternatives *
-rw-r--r-- 1 root root 1071840 2008-03-05 18:52 available
-rw-r--r-- 1 root root 1069981 2008-03-05 18:07 available-old
-rw-r--r-- 1 root root       8 2007-10-16 00:17 cmethopt
-rw-r--r-- 1 root root    2552 2008-03-03 20:06 diversions
-rw-r--r-- 1 root root    2623 2008-03-03 20:02 diversions-old
drwxr-xr-x 2 root root  217088 2008-03-05 18:52 info  *
-rw-r----- 1 root root       0 2008-03-06 17:07 lock
drwxr-xr-x 2 root root    4096 2007-09-21 21:21 parts
-rw-r--r-- 1 root root      30 2007-10-16 00:26 statoverride
-rw-r--r-- 1 root root       0 2007-10-16 00:17 statoverride-old
-rw-r--r-- 1 root root 1117072 2008-03-05 18:52 status
-rw-r--r-- 1 root root 1115197 2008-03-05 18:07 status-old
drwxr-xr-x 2 root root    4096 2008-03-05 04:47 triggers  *
drwxr-xr-x 2 root root    4096 2008-03-05 18:52 updates  *
  
* = pale blue
:confused:

---

### Post by Oldsoldier2003 on 2008-03-06
> **leebra said:**
> :/var/lib/dpkg$ ls -l
total 4544
drwxr-xr-x 2 root root    4096 2008-03-03 19:51 alternatives *
-rw-r--r-- 1 root root 1071840 2008-03-05 18:52 available
-rw-r--r-- 1 root root 1069981 2008-03-05 18:07 available-old
-rw-r--r-- 1 root root       8 2007-10-16 00:17 cmethopt
-rw-r--r-- 1 root root    2552 2008-03-03 20:06 diversions
-rw-r--r-- 1 root root    2623 2008-03-03 20:02 diversions-old
drwxr-xr-x 2 root root  217088 2008-03-05 18:52 info  *
-rw-r----- 1 root root       0 2008-03-06 17:07 lock
drwxr-xr-x 2 root root    4096 2007-09-21 21:21 parts
-rw-r--r-- 1 root root      30 2007-10-16 00:26 statoverride
-rw-r--r-- 1 root root       0 2007-10-16 00:17 statoverride-old
-rw-r--r-- 1 root root 1117072 2008-03-05 18:52 status
-rw-r--r-- 1 root root 1115197 2008-03-05 18:07 status-old
drwxr-xr-x 2 root root    4096 2008-03-05 04:47 triggers  *
drwxr-xr-x 2 root root    4096 2008-03-05 18:52 updates  *
  
* = pale blue
:confused:
looks like your permissions are correct, try removing yourself from the root group, as there is no real reason to be part of that group. this might actually fix the problem. If it doesn't you could try starting in recovery mode as root and running:

```
dpkg --configure -a
apt-get update
apt-get upgrade
```

If both of these fail, I'm at the endof my knowledge on how to fix the problem, I wouldn't feel comfortable having you use any of the --force- options as I'm not familiar enough to give you a way to fix it without risking breaking your system even more.

---

### Post by jimv on 2008-03-06
I think you need to run a disk check.

Boot from the Ubuntu CD and in a terminal, run:

sudo fsck -py hda1

(if your partition isn't hda1, then replace it with the appropriate one.  Also, make sure that your HD isn't mounted.)

---

