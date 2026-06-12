---
title: "interesting permission problem"
date: 2008-01-17
forum: General Help
---

### Post by Zacharias on 2008-01-17
root@shibumi-laptop:~# /etc/fstab
bash: /etc/fstab: Permission denied

i tried  chown root /etc/fstab

but still no permission. Also my ext3 partition (other) i cannot write on it. 

i cannot paste my akregator file into /usr/share.... because of permission :(

what is my false ? how can i fix it ?

thanks

---

### Post by dgray_from_dc on 2008-01-17
Are you trying to edit /etc/fstab?  Because this

> root@shibumi-laptop:~# /etc/fstab

means that you are tyring to execute it as a program.

Logged in as root like you are, you should be able to type

```
gedit /etc/fstab
```
     or
```
nano /etc/fstab
```
     or
```
vim /etc/fstab
```

---

### Post by Zacharias on 2008-01-17
ok thanks, 

what about my other ext3 harddrive ? i cannot give permission of write.

---

### Post by dgray_from_dc on 2008-01-17
Is it internal?  If so, I suggest setting that up in fstab.  Read the man page for details

```
man fstab
```

If not the chmod command may help.

```
man chmod
```

---

### Post by geirha on 2008-01-17
The output of the following will help figuring out your problem:
```
sudo fdisk -l  # Lists all harddrives and partitions
cat /etc/fstab # Lists how you intend to mount the partitions
mount          # Lists the currently mounted filesystems 

```
(please put the output inside [code]-tags)

---

