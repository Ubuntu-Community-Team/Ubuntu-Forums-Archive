---
title: "chown not permitted bitornado can't start"
date: 2007-01-10
forum: General Help
---

### Post by fokuslee on 2007-01-10
Here is my problem i mounted my fat32 partition at /media /sda3 
/etc/fstab reads 
/dev/sda3       /media/sda3     vfat iocharset=utf8,umask=000   0        0

sda3 is owned by root 
but i unasked so i can read write just fine under normal conditions but i need to change the ownership to myself so that bittorando can start correctly.  
and here is where the trouble began

fokuslee@fokuslee-ubuntu:~$ sudo chown -R fokuslee:fokuslee /media/sda3
Password:
chown: changing ownership of `/media/sda3': Operation not permitted
fokuslee@fokuslee-ubuntu:~$ dmesg | grep panic
fokuslee@fokuslee-ubuntu:~$
fokuslee@fokuslee-ubuntu:~$ sudo -i
root@fokuslee-ubuntu:~# chown -R fokuslee:fokuslee /media/sda3
chown: changing ownership of `/media/sda3': Operation not permitted

so i do i change the owner?

---

### Post by Jussi Kukkonen on 2007-01-10
fat32 doesn't support permissions, does it? It would make sense that you can't change them. 

Use the mount options (sorry, don't remember which) to set the "ownership".

---

### Post by bettlebrox on 2007-01-10
This should work:

sudo mount -o remount,user=fokuslee /media/sda3

---

### Post by fokuslee on 2007-01-11
oh and bettlebrox ur code did not work for me : (

uh if i put uid=fokuslee would that do the same thing 
i  am just tossing out ideas don't no if it works 
i no the user options is to enable mounting by user

---

### Post by Jussi Kukkonen on 2007-01-11
> **fokuslee said:**
> oh and bettlebrox ur code did not work for me : (

uh if i put uid=fokuslee would that do the same thing 
i  am just tossing out ideas don't no if it works 
i no the user options is to enable mounting by user

You are getting close. use the command ***id*** to find out your *uid* and *gid* and use those in your mount command (something like* uid=1000.gid=1000*)

---

### Post by fokuslee on 2007-01-11
Jussi Kukkonen 
u r my HERO  thx mate 
it worked finally 

interestingly i even made a symlink to the folder which is owned by me still bittorent refuse to write to it .
anyways thx again

---

