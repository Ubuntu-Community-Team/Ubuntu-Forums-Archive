---
title: "New to Ubuntu - HD issues"
date: 2005-11-01
forum: General Help
---

### Post by Naitsirc on 2005-11-01
I've just finished installing Ubuntu 5.04 and I find it very good, and also I'm trying to figure how to use it and how to get the best of the S.O...

I have a second HD (internal) plugged in the machine, but I can't manage to locate it or even to see if it is recogniced; I found this rare because in the instalation, both HD's were recogniced, but once the Ubuntu S.O is running, I cannot locate my second HD...:confused: 

Can you help me with this?

Thank you!

---

### Post by Schmots on 2005-11-01
here is where a bit of unix knowledge comes in.

Lets assume ide shall we

the first chain first channel is hda
second channel hdb

second chain first channel hdc
second channel hdd

so if this harddrive is on the same channel as your primary hd and it has one partition you can do this

sudo mkdir /mnt/hdb1
sudo mount /dev/hdb1 /mnt/hdb1

That should get you started

---

### Post by Naitsirc on 2005-11-02
My hdb has two partitions...I tryed to get it started as you suggested, but it didn't work; the terminal sends me this mesage: 

 # sudo mkdir /mnt/hdb1
 # sudo mount /dev/hdb1/hdb1
mount: can't find /dev/hdb1/hdb1 in /etc/fstab or /etc/mtab

I guess it is not recogniced because of the two partitions. Is there another way to do it?

Thanks pal!!

---

### Post by Naitsirc on 2005-11-02
I found the HD in the Device Manager, but still I cannot find a way to open it...:(

---

### Post by kemosabe79 on 2005-11-02
#sudo mkdir /mnt/hdb1
#sudo mount /dev/hdb1 /mnt/hdb1

not,

# sudo mkdir /mnt/hdb1
# sudo mount /dev/hdb1/hdb1

You didnt mount the drive if you typed that in your terminal:smile:

---

### Post by Naitsirc on 2005-11-02
hehe, a little detail...but still is not working:???: ...it displays:

mount: mount point mnt/hdb1 does not exist

what else you suggest i can do??

---

