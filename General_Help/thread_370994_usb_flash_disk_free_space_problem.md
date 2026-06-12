---
title: "usb flash disk free space problem"
date: 2007-02-26
forum: General Help
---

### Post by fouadk on 2007-02-26
i have a usb flash disk that is 256 mb as free space coz it is emty

on windows it shows that it have 256 mb of free space while on ubuntu it shows that it only have 17 mb of free space

what is the problem and how can i resolve it???

is there is a way to format it ???

what is the solution???

Thanks in advance

---

### Post by taurus on 2007-02-26
Did you store something on it and remove it in Ubuntu?  What's the output of this command from a terminal?

```
df -h
```

---

### Post by fouadk on 2007-02-26
```
Filesystem            Size Used Avail Use% Mounted on
/dev/hda2             9.7G  3.1G  6.1G  34% /
varrun                126M   84K  126M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M   96K  126M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-28-386/volatile
/dev/hda3             934M  425M  460M  49% /home
/dev/hda1              64G  7.7G   56G  13% /media/hda1
/dev/sda              249M  232M   17M  94% /media/1

```

the device im having problem with is /dev/sda, above it says that it have 249 original capacity with 232 used and the remaining is 17 but when i explore it, it is empty so does in windows

please help

Thanks in advance

---

### Post by taurus on 2007-02-26
What's the output of these commands from a terminal?

```
ls -la /media/1
du -h /media/1
```

---

### Post by fouadk on 2007-02-26
```
fouad@SUPER:~$ ls -la /media/1
total 8
drwx------ 2 fouad fouad 4096 1970-01-01 02:00 .
drwxr-xr-x 5 root  root  4096 2007-02-26 22:45 ..
fouad@SUPER:~$ du -h /media/1
4.0K    /media/1
fouad@SUPER:~$
```

---

### Post by taurus on 2007-02-26
Try

```
sudo du -h /media/1
```
Otherwise, reformat it again in Windows.

---

