---
title: "admin rights"
date: 2007-01-01
forum: General Help
---

### Post by b1ackhawk on 2007-01-01
i am running ubuntu on my home box, and want to mount my storage partition for my movies music and what not, but i dont have rights to edit fstab, any suggestions? i have full root rights, i also cant make directories in certain places?

---

### Post by meng on 2007-01-01
If your primary user has administrative rights, then you can edit such files by prefacing the edit command with sudo:
e.g.
sudo vim /etc/fstab
or
sudo nano /etc/fstab
or
gksu gedit /etc/fstab
(gksu is recommended for starting GUI programs with superuser privileges)

When asked for a password, enter the user password.

---

### Post by melancholeric on 2007-01-01
sudo nano /etc/fstab

sudo mkdir

then type the password

edit: too slow

---

### Post by b1ackhawk on 2007-01-01
still having problems after trying that stuff, is there a different way of mounting a partition?


i tried 

sudo vim /etc/fstab

it gave me tons of crap of recovery that didnt work

---

### Post by meng on 2007-01-01
> **b1ackhawk said:**
> still having problems after trying that stuff, is there a different way of mounting a partition?
I don't know which way you tried already, perhaps you could tell us in more detail.

---

### Post by b1ackhawk on 2007-01-01
i added an edit i also tried

sudo mkdir ... 

but thats a seperate less of a prblm

---

### Post by meng on 2007-01-01
> **b1ackhawk said:**
> i added an edit i also tried
sudo mkdir ... 
but thats a seperate less of a prblm
Okay, you're making me "fill in the blanks" here, but I'm going to assume that you mean that you edited the fstab and created the mountpoints. Well of course nothing's been mounted yet unless you have already rebooted (which you didn't specify) or else run the command:
sudo mount -a

---

### Post by b1ackhawk on 2007-01-01
i told you what i tried in an ealier post

sudo vim /etc/fstab

it gave me a bunch of crap, aka didnt work. cant figure out how to edit it still

---

