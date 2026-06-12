---
title: "no-ip"
date: 2008-02-21
forum: General Help
---

### Post by taimur on 2008-02-21
hi i cannot install no-ip can you tell me how to do it?



root@ubuntu-desktop:~# sudo apt-get install no-ip
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package no-ip

---

### Post by taurus on 2008-02-21
Do you have all the repos enable in /etc/apt/sources.list?  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.  

Now run

```
sudo apt-get update
sudo apt-get install no-ip
```

---

### Post by taimur on 2008-02-23
i have done it i make it install but how to use no-ip
how to configure it
how to check it's status
and how to put host

---

