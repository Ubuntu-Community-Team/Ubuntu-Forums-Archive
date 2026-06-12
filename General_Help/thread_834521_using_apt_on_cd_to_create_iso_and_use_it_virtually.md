---
title: "using apt on cd to create iso and use it virtually"
date: 2008-06-19
forum: General Help
---

### Post by dstar on 2008-06-19
Hi
I need some help.
I am using ubuntu 8.4.I have downloaded a lot of packages and saved them in a iso file using apt on cd and i have copied that iso on the usb drive.
Now my HDD got damaged and i have installed new copy of ubuntu now the problem is that in location where i am their is no fast internet connection (all are 52K dial up)so how can i use that iso file created by atponcd to get the packages installed.


In short how do i add a virtual cd-rom and install an iso in it

P.S:in windows it can be done using software like Virtual Cd,Daemon Tools or alcohol

---

### Post by jualin on 2008-06-19
If you want to mount you need to use the following command

> sudo mount debianetch.iso /media/isoimage/ -t iso9660 -o loop

In the above command you can replace debianetch.iso to your own iso image.

---

### Post by dstar on 2008-06-20
Ok i did the same as you told be but it gave me the following error

> mount: mount point /media/isoimage/ does not exist

---

### Post by gruffy-06 on 2008-06-20
You must create a folder for any filesystem to be mounted. Create a folder named isoimage in /media/. Then try mounting your iso file again.

---

### Post by cariboo on 2008-06-20
You have to do it in two steps. First mount you usb drive. then once your dirve is mount you can mount the iso using the following command in a terminal:

```
sudo mount -o loop /media/disk/some.iso /mnt
```

where /media/disk is your mounted usb drive, some.iso is the name of your iso file, /mnt doesn't seem to get used for anything any more so I use that, but you can use any directory you want.

Jim

---

