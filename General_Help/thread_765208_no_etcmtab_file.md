---
title: "no /etc/mtab file"
date: 2008-04-24
forum: General Help
---

### Post by roberto73 on 2008-04-24
Hi,
I can't mount anymore.

Every time I plug a usb drive in... 
This is what I got:
```
unable to mount the volume "STICK".
mount: can't open /etc/mtab for writing:
no such file or directory
```
...Same problem using the shell

fdisk looks good but but the system monitor shows no mounted partitions.

```
roberto@arabidopsis:~$ sudo df -a
df: cannot read table of mounted file systems: No such file or directory 
```

I tried to create a /etc/mtab file by myself:

```
roberto@arabidopsis:~$ sudo touch /etc/mtab
touch: cannot touch `/etc/mtab': No such file or directory
```

Several reboots did not fix the problem!

I need help! :(
thanx

---

### Post by roberto73 on 2008-05-19
> I tried to create a /etc/mtab file by myself:

```
roberto@arabidopsis:~$ sudo touch /etc/mtab
touch: cannot touch `/etc/mtab': No such file or directory
```



I used the rescue-mode of an alternate cd... using the root shell I was able to create the mtab file... and this solved the problem :)

---

