---
title: "I lokst admin"
date: 2007-07-16
forum: General Help
---

### Post by C-{pR0F on 2007-07-16
Heloo , I've deleted the oem user that come with the installation , and i had now just one user that don't have any admin privilages , and i can't do anything with , i created this user when i first install ubuntu , but it don't have any privilages ,  i tried the oem-config-prepare from the root at the recovery mode , and it didn't work , 

How do i create a new admin user :confused:

---

### Post by giacomo on 2007-07-16
You could boot you system with a linux live cd (for these recovery tasks I prefer minimal systems without X).
Mount your partition:
```
mkdir /mnt/hd_root
mount /dev/hd? /mnt/hd_root
```
Change the root:
```
chroot /mnt/hd_root /bin/bash
```
Create an user account:
```
useradd -m -G users your_name
passwd your_name
```
Exit and reboot:
```
exit
umount /mnt/hd_root
reboot
```

(rembember to remove the livecd from the cd-reader)

Bye.

---

### Post by C-{pR0F on 2007-07-16
but that don't give admin privilages ,,,,, 
i just  want to create a user that have an adminstarion privilages or how can i add adminstarion privilages to an existing user.


(i can use the root from the recovery mode , but i'm still new to linux and don't know how to do that)

---

### Post by sisco311 on 2007-07-16
> how can i add adminstarion privilages to an existing user```
sudo adduser *user_name* admin
```where *user_name* is an existing user

---

### Post by bapoumba on 2007-07-16
From grub menu, boot in recovery mode. You'll be root with a # prompt.
```
# adduser <insert_here_your_user_login> admin
# reboot
```

Once you are logged in your graphic session, add yourself to the following default groups:
```
~$ groups
bapoumba adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
```

```
~$ sudo adduser <insert_here_your_user_login> <insert_a_group_here>
```

---

### Post by C-{pR0F on 2007-07-17
oh that works bapoumba
thankx

---

### Post by bapoumba on 2007-07-17
You're welcome. Glad to see you fixed it.
Side note: sudo oem-config-prepare has to be run from the oem user ;)

---

