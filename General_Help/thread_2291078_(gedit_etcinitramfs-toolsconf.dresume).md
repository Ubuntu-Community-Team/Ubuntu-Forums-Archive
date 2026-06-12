---
title: "(gedit /etc/initramfs-tools/conf.d/resume)"
date: 2015-08-17
forum: General Help
---

### Post by al14 on 2015-08-17
I went to edit my (gedit /etc/initramfs-tools/conf.d/resume) but it's an empty file...

What to do?

Thanks in advance!

---

### Post by pqwoerituytrueiwoq on 2015-08-17
as a example it should look like this
```
RESUME=UUID=**75407416-7746-4DFF-9C7C-462BC732F1C0**
```
the long number is the UUID for your swap partition
this command will get you the UUID
```
~$ sudo blkid |grep 'TYPE="swap"'
/dev/sdc1: LABEL="Swap" UUID="**75407416-7746-4dff-9c7c-462bc732f1c0**" TYPE="swap"
```
you can use this command to crate the fiel with the correct content
```
echo RESUME=UUID=**75407416-7746-4DFF-9C7C-462BC732F1C0**  | sudo tee /etc/initramfs-tools/conf.d/resume
```
jsut change the long number to match yours

---

### Post by al14 on 2015-08-18
@pqwoerituytrueiwoq

Worked like a charm!

Thanks!!  :D

---

