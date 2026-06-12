---
title: "[SOLVED] cannot mount Hardisk in ubuntu live"
date: 2007-10-16
forum: General Help
---

### Post by underdog512 on 2007-10-16
I am trying to recover some data from the hard drive of a windows box that has a corrupted kernal.  I am using a live CD of ubuntu 6.06.  I can't seem to mount the harddirve in order to read the files.  

I tried:

sudo mount /dev/hda1 /home/ubuntu

but it didn't work.  

any ideas?  would I have same issues if I used Knoppix?

---

### Post by Pumalite on 2007-10-16
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by bodhi.zazen on 2007-10-16
That is an unusual mount point.

First, to list your partitions,

```
sudo fdisk -l
```

Then :

```
sudo mkdir /media/ubuntu
sudo mount /dev/hda1 /media/ubuntu || sudo mount /dev/sda1 /media/ubuntu
ls /media/ubuntu
```

---

### Post by underdog512 on 2007-10-16
I mounted it successfully but I still cannot access the data because of permission issues.  I tried chmod 777 /media/ubuntu but it just says that it is a read only file system and nothing happens.

---

### Post by bodhi.zazen on 2007-10-16
You should be able to access the data as root :

```
gksu nautilus /media/ubuntu
```

did you chmod as root ?

```
sudo chmod -r 777 /media/ubuntu
```

don't forget the recursive ( -r ) flag

---

### Post by underdog512 on 2007-10-17
this is resolved thanks for the help

---

