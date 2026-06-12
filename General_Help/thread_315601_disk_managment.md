---
title: "disk managment"
date: 2006-12-09
forum: General Help
---

### Post by peebly on 2006-12-09
Where is the disk management program in edgy.

Dapper had one.

---

### Post by ThrobbingBrain66 on 2006-12-09
If you are talking about Gparted for moving, resizing, creating/deleting partitons, you have to install it from the repos.

```
sudo apt-get install gparted
```

---

### Post by peebly on 2006-12-09
Dapper used to have a little program under preferences or administration which would show your installed disks etc.

Basically I have a spare hard disk which I have stuck in the computer, The one which windows used to accommodate until I ditched it completely for Linux:p .

Have already formated the disk with gparted, but its not showing under my computer.

---

### Post by MrPyro321 on 2006-12-09
> **peebly said:**
> Dapper used to have a little program under preferences or administration which would show your installed disks etc.

System>Administration>Disks

Is that what you are looking for?


EDIT: Whoops my bad i thought you said your running Dapper

---

### Post by catdriver on 2007-05-14
> **MrPyro321 said:**
> System>Administration>Disks

Is that what you are looking for?


EDIT: Whoops my bad i thought you said your running Dapper

I believe that's what he's looking for... Me too, I'm just up on Fiesty.... and need to access a second partition on my HD.  It's there under gparted, and will mount to /media/disk, that's what it's called, I don't know why... But it's owned by root, a sudo chown <myuser> /media/disk doesn't do what I expected, but also doesn't return any errors.  Basically chown it to my user  and make it read write executeable... Anyone wanna pitch in...

---

### Post by zakarov on 2007-05-14
Where did the system -> administration -> disks utility go to? I liked it better than gparted or qtparted, but it doesn't seem to be in fiesty.

---

### Post by zakarov on 2007-05-14
Oh, found it

[http://flomertens.free.fr/disk-manager/download.html](http://flomertens.free.fr/disk-manager/download.html)

---

### Post by psusi on 2007-05-14
I think the disk manager was removed because it was basically a useless pile of crap.  You can use gparted to manage your disks.

---

### Post by zakarov on 2007-05-14
is there a way to specify a path for mounting the partition in gparted?

---

### Post by strabes on 2007-05-15
> **zakarov said:**
> is there a way to specify a path for mounting the partition in gparted?

Mount locations are in your /etc/fstab. Run ```
sudo gedit /etc/fstab
``` to edit it.

---

