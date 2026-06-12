---
title: "How do I format my sata hard drive"
date: 2008-04-20
forum: General Help
---

### Post by TheMixtureMedia on 2008-04-20
Hi there i just moved my sata drive from one linux box and to another and it is my slave drive now and it says i am not the owner of the drive and i can not delete files off of this drive how do i fix this??

---

### Post by gsiliceo on 2008-04-20
try running nautilus as root
in terminal
> sudo nautilus
And then go to /media/YOURDRIVE**

---

### Post by gsiliceo on 2008-04-20
And also don't forget to change the ownership, right click on the files/properties.

---

### Post by TheMixtureMedia on 2008-04-20
It will not let me its says i am not the owner and i do not have permission to do this

---

### Post by sisco311 on 2008-04-20
To change the owner of an ext3/ext2 partition open a terminal and type:
```
sudo chown -R <your_username>\: <mount-point-of the-partition>
```Replace *<your_username*> with your user name and <mount-point-of the-partition> with the folder name where the partition is mounted.

example:
```
sudo chown -R TheMixtureMedia\: /media/disk
```If the partition if formatted to ntfs or fat (or your not sure) post the output from:
```
mount
``````
sudo fdisk -l
``````
cat /etc/fstab
```

---

### Post by TheMixtureMedia on 2008-04-21
I am tring what you are telling me to do and it will not let me do it any ideas I really want to use this drive.

---

### Post by sisco311 on 2008-04-21
post the output of this commands:

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by banished_one on 2008-04-21
you can easily format by booting from a os cd (ubuntu, windows what ever) they alwyas have a format then install option, format the drive and then exit the install. I know its not a nice way to do it but it doesnt require any skill :)

---

