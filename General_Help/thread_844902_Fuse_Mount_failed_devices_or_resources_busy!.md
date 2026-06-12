---
title: "Fuse: Mount failed devices or resources busy!??"
date: 2008-06-30
forum: General Help
---

### Post by morbid_bean on 2008-06-30
after manually setting up my slave hard drive to auto mount i still am unable to succeed...during boot I get this error on a list of things that show up something like  "Fuse: mount failed devices or resources busy" then at the far right will say FAIL in red...what is this? and how do i fix it

---

### Post by mempman on 2008-06-30
this just means that someone, or some process, is using this device, and thusly, it cannot be unmounted.

To figure out what/or who is using a certain device, use the following command:

fuser -vm /DEVICE

---

### Post by morbid_bean on 2008-06-30
> **mempman said:**
> this just means that someone, or some process, is using this device, and thusly, it cannot be unmounted.

To figure out what/or who is using a certain device, use the following command:

fuser -vm /DEVICE

I get this output:

```
Cannot stat /DEVICE: No such file or directory
Cannot stat /DEVICE: No such file or directory
Cannot stat /DEVICE: No such file or directory

```

---

### Post by morbid_bean on 2008-06-30
bump

---

### Post by morbid_bean on 2008-06-30
bump :(

---

### Post by morbid_bean on 2008-06-30
...

---

### Post by avtolle on 2008-06-30
DEVICE as used in mempman's post refers to the device name, e.g., /dev/sda.

---

### Post by morbid_bean on 2008-06-30
thanks alot but heres what happens   ```
jimbo@Monster:~$ fuser -vm /dev/sdb1
jimbo@Monster:~$ 

```

EDIT: ok nvm i forgot the sudo part

---

### Post by morbid_bean on 2008-06-30
is wut i get 


```
jimbo@Monster:~$ sudo fuser -vm /dev/sdb1
                     USER        PID ACCESS COMMAND
/dev/sdb1:           root       4354 F.... mount.ntfs-3g
jimbo@Monster:~$ 

```

---

### Post by mempman on 2008-06-30
> **morbid_bean said:**
> is wut i get 


```
jimbo@Monster:~$ sudo fuser -vm /dev/sdb1
                     USER        PID ACCESS COMMAND
/dev/sdb1:           root       4354 F.... mount.ntfs-3g
jimbo@Monster:~$ 

```

So that basically means that process#4354 is using this device you are trying to unmount, and you will have to kill this process or you won't be able to unmount.  The process was initiated by the mount command,  That pretty much what it's telling you.

---

