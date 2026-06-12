---
title: "Mounting a Fat partition, Edgy Eft"
date: 2007-02-10
forum: General Help
---

### Post by boris yeltsin on 2007-02-10
I've been trying, in vain, to help my friend mount a drive on Ubuntu 6.10. We've tried several of the standard methods (just plain mounting it, adding it into that partition list file in /etc/) and even tried that automatic script, and none of them worked. Does anyone have any idea how we could go about mounting this partition? Here is the fdisk output:

[IMG]http://i3.tinypic.com/30ctzrs.png[/IMG]

I think the fact that it's FAT16 is the problem, but seeing as he there's already files on there, I don't know if we'd want to convert the filesystem at the time. 

To clarify, we are trying to mount hdb1.

---

### Post by nickoli_02 on 2007-02-10
Does the drive mount at all? 

```
sudo mount /dev/hdb1 /media/hdb1
```

that will mount your fat16 drive. You may get an error saying /media/hdb1 doesn't exist, you'll just have to create the folder

```
mkdir /media/hdb1
```

---

### Post by boris yeltsin on 2007-02-10
> **nickoli_02 said:**
> Does the drive mount at all? 

```
sudo mount /dev/hdb1 /media/hdb1
```

that will mount your fat16 drive. You may get an error saying /media/hdb1 doesn't exist, you'll just have to create the folder

```
mkdir /media/hdb1
```


We tried mounting it to a directory we created called /media/fat16, and that didn't seem to work. Using that same method we managed to mount hda1 to /media/windows, but it didn't seem to work the same way for hdb1.

---

### Post by gradedcheese on 2007-02-10
Don't forget to tell mount about the filesystem type:

sudo mkdir -p /media/hdb1
sudo mount **-t vfat** /dev/hdb1 /media/hdb1

what do you get?  any error messages?

---

### Post by nickoli_02 on 2007-02-10
Thanks gradedcheese, I thought I missed something :P

---

