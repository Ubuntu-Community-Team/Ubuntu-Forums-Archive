---
title: "Mounting a shared window folder in Ubuntu"
date: 2008-02-02
forum: General Help
---

### Post by thirunavukkarasu on 2008-02-02
Hi,

i have a shared folder on my Win XP machine. i can mount the same using #mount //ip_of_machine/folder /mnt directory sucessfully in suse and Redhat.

But when the same is executed in Ubuntu it shows that wrong filesystem specified. How can i mount my remote shared folder on Window XP to Ubuntu machine. 

Thanks! 

Regards,
Thiru.S

---

### Post by SpiderGorilla on 2008-02-02
I assume you've got Samba running, right?

---

### Post by jan quark on 2008-02-02
run in terminal

```
mount
```

```
sudo fdisk -l
```

and post the result plase

---

### Post by jan quark on 2008-02-02
sry missed the samba point

---

### Post by thirunavukkarasu on 2008-02-06
Hi guys,

Installing smbfs package has resolved the issue. 

apt-get install smbfs

Now i can able to mount my windows shared folder to Ubuntu machine through lan. 

Also spidergorilla, how to know my samba is running or not? 

Regards
Thiru.S

---

