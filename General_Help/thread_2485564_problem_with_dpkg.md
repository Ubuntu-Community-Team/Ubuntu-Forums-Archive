---
title: "problem with dpkg"
date: 2023-04-02
forum: General Help
---

### Post by jgw on 2023-04-02
I was told to run dpkg --configure -a and you can see what I got.

This is another read-only file thing but I am not sure what file system its referencing.  As far as I can tell dpkg is a program and now, apparently, its also 

root@greg3:/var/lib# dpkg --configure -a
dpkg: error: unable to access the dpkg database directory /var/lib/dpkg: Read-only file system
root@greg3:/var/lib# 

Options marked [*] produce a lot of output - pipe it through 'less' or 'more' !
root@greg3:/var/lib# ls -l dpkg
total 5556
drwxr-xr-x 2 root root    4096 Mar 31 12:17 alternatives
-rw-r--r-- 1 root root      11 Oct  4 12:28 arch
-rw-r--r-- 1 root root  215157 Aug  9  2022 available
-rw-r--r-- 1 root root       8 Aug  9  2022 cmethopt
-rw-r--r-- 1 root root     616 Oct  4 12:31 diversions
-rw-r--r-- 1 root root     671 Oct  4 12:31 diversions-old
drwxr-xr-x 2 root root  471040 Mar 31 15:11 info
-rw-r----- 1 root root       0 Mar 31 15:10 lock
-rw-r----- 1 root root       0 Mar 31 15:10 lock-frontend
drwxr-xr-x 2 root root    4096 Apr  6  2022 parts
-rw-r--r-- 1 root root     200 Aug  9  2022 statoverride
-rw-r--r-- 1 root root 2476069 Mar 31 12:17 status
-rw-r--r-- 1 root root 2476065 Mar 31 09:18 status-old
drwxr-xr-x 2 root root    4096 Mar 24 01:09 tmp.ci
drwxr-xr-x 2 root root    4096 Mar 31 15:11 triggers
drwxr-xr-x 2 root root    4096 Mar 31 15:11 updates
root@greg3:/var/lib# bash <(curl -s https://gitlab.com/Shinobi-Systems/Shinobi-Installer/raw/master/shinobi-install.sh)^C

---

### Post by Bashing-om on 2023-04-02
Hey jgw :)

These things happen - for a reason.
When I encounter such the first thing I do is verify the file system integrity with a file system check/repair.

```

sudo fdisk -lu

```
to know the file system type and partitioning.
If it is "ext4"; sic fsck on the partition(s).

When that comes back clean then look at what file permissions are set.

[INDENT]my bit to try and help
[/INDENT]

---

### Post by jgw on 2023-04-05
sudo fdisk -lu

[https://pastebin.ubuntu.com/p/RdP9VrsKW3/](https://pastebin.ubuntu.com/p/RdP9VrsKW3/)

---

### Post by Bashing-om on 2023-04-05
jgw; welp ---

Looks that your ubuntu is installed on the 3rd drive.
Boot a liveUSB in "try ubuntu" mode - and in terminal run:
```

sudo fsck /dev/sdc3

```

What results ?

[INDENT]could be Yes, all done
might be, more needed
[/INDENT]

---

### Post by jgw on 2023-04-17
Thank you for the replies!

I stopped using apt and apt-get when installing stuff and switched to aptitude and that seemed to clean up my messes.  I will mark this one as solved.

---

### Post by Bashing-om on 2023-04-17
jgw 

Yay :D

Good deal

---

