---
title: "Home folder is full ?"
date: 2008-07-05
forum: General Help
---

### Post by abukhallad on 2008-07-05
Hi guys .


I've problem in Ubuntu8,04 with Home Folder?
Look at attachments ,please .


:popcorn:
Enjoy!

---

### Post by LinuxRocks713 on 2008-07-05
What's the output of

```

df -h

```
?

Also, is it your data that is filling up the drive or your hidden folders?

---

### Post by abukhallad on 2008-07-05
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.8G  4.1G  2.5G  63% /
varrun                501M  108K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   68K  501M   1% /dev
devshm                501M  360K  501M   1% /dev/shm
lrm                   501M   38M  464M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7             989M  937M  2.0M 100% /home
gvfs-fuse-daemon      6.8G  4.1G  2.5G  63% /home/abdallah/.gvfs
/dev/sda8              83G   20G   63G  24% /media/disk
/dev/sda2              49G   30G   20G  60% /media/SQ004547V02

```

> Also, is it your data that is filling up the drive or your hidden folders? 
I think it might be Hidden Folders .

```
[COLOR="Red"]gvfs-fuse-daemon      6.8G  4.1G  2.5G  63% /home/abdallah/.gvfs[/COLOR]
```

---

### Post by Elfy on 2008-07-05
It's not that file - that is some sort of odd thing, which I can't remember the reason for :D

If /home is full then you need to do something about files that are in there or resize it.

Edit - been of to look 

> It's a special directory which has mounts of network locations for using with programs that don't use GVFS itself.

alos if you look at your df -h ther is no way the file is there
/dev/sda7             989M  937M  2.0M 100% /home
gvfs-fuse-daemon      6.8G  4.1G  2.5G  63% /home/abdallah/.gvfs

your /home is only 989Mb - you can't fit 4.1Gb in to your /home :)

---

### Post by chrisccoulson on 2008-07-05
What is the output of:
```
sudo du -h -x --max-depth=1 /home
```

---

### Post by abukhallad on 2008-07-05
```
sudo du -h -x --max-depth=1 /home
```


```
du: cannot access `/home/abdallah/.gvfs': Permission denied
920M	/home/abdallah
16K	/home/lost+found
920M	/home

```

---

### Post by chrisccoulson on 2008-07-05
Looks like the space is all accounted for. There's 920MB of data in /home/abdallah. You'll need to go through your home folder to clear some space

---

### Post by abukhallad on 2008-07-05
OK .

Thanks

I'll try to add more space .

---

