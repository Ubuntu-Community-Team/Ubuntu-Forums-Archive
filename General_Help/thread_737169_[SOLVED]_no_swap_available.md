---
title: "[SOLVED] no swap available"
date: 2008-03-27
forum: General Help
---

### Post by MONODA on 2008-03-27
Hi when I installed gutsy a while I back, I gave it 3.8 gb of swap. It has been mounted as swap for as long as I can remmeber but now when I open system monitor it says that 0 swap is used of 0. I can make swap on with gparted but then I have to do this each time which gets annoying. How can I fix this?

---

### Post by jakev383 on 2008-03-27
You'll need to list it in /etc/fstab 
Example:

```

# /dev/sdb1
UUID=b18d176b-7ef0-423e-9e53-512f0feeab44 none            swap    sw              0       0

```

---

### Post by kpkeerthi on 2008-03-27
Find your swap partition using ```
sudo fdisk -l
```
If **/dev/sda2** is listed as swap from the above command, type ```
sudo swapon /dev/sda2
```

To make the change permanent add /dev/sda2 to fstab
```
gksudo gedit /etc/fstab
```
Add the below line
```
/dev/sda2  none  swap  sw  0  0
```
Save and Exit. Reboot.

---

### Post by MONODA on 2008-03-27
yes I have all of that but it still does not work...

---

### Post by wolfen69 on 2008-03-27
same problem solved here [http://ubuntuforums.org/showthread.php?t=553676&highlight=activate+swap](http://ubuntuforums.org/showthread.php?t=553676&highlight=activate+swap)

---

### Post by kpkeerthi on 2008-03-27
> **MONODA said:**
> yes I have all of that but it still does not work...

What happens when you type ```
sudo mount -a
```?

---

### Post by MONODA on 2008-03-28
when I type sudo mount -a i get:
Failed to access '/dev/disk/by-uuid/2C88743C8874071C': No such file or directory

---

### Post by kpkeerthi on 2008-03-28
> **MONODA said:**
> when I type sudo mount -a i get:
Failed to access '/dev/disk/by-uuid/2C88743C8874071C': No such file or directory

Just follow my instruction in the previous [post# 3]("http://ubuntuforums.org/showpost.php?p=4597319&postcount=3")

---

### Post by MONODA on 2008-03-28
yes I did that but it did not help, I went to the thread linked to by wolfen69 and fixed it thanks anyway.

---

### Post by kpkeerthi on 2008-03-28
> **MONODA said:**
> when I type sudo mount -a i get:
Failed to access '/dev/disk/by-uuid/2C88743C8874071C': No such file or directory

You have been using invalid UUID. My post #3 suggest you to use **device name** if you look carefully.

---

### Post by MONODA on 2008-03-28
alright I will try that

---

