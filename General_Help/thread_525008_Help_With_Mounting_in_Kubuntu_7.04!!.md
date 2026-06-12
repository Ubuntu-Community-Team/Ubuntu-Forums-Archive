---
title: "Help With Mounting in Kubuntu 7.04!!"
date: 2007-08-13
forum: General Help
---

### Post by Atrio05 on 2007-08-13
sorry if I'm posting this in the wrong area but i really need help with this. i am kinda new to kde and i need help getting my external USB hdd to mount so i can at least see whats on there(but i would like read/write privileges) i can't seem to find how i change the permissions to the drive. oh and now the system settings Disk & Filesystems keeps hanging when i try to go into admin mode.

PS. it is a ntfs drive and i had no problems with it automounting in ubuntu and i also had read/write privileges 

someone please help i really want to use kubuntu but so far i've had nothing but problems with it!!

---

### Post by Happy_Man on 2007-08-13
> **Atrio05 said:**
> sorry if I'm posting this in the wrong area but i really need help with this. i am kinda new to kde and i need help getting my external USB hdd to mount so i can at least see whats on there(but i would like read/write privileges) i can't seem to find how i change the permissions to the drive. oh and now the system settings Disk & Filesystems keeps hanging when i try to go into admin mode.

PS. it is a ntfs drive and i had no problems with it automounting in ubuntu and i also had read/write privileges 

someone please help i really want to use kubuntu but so far i've had nothing but problems with it!!
Hmmm... how about mounting it using a Terminal? Just go to System --> Konsole, and type ```
sudo mkdir /media/ntfs
sudo mount /dev/sda<partition number> /media/ntfs
```

---

### Post by merlinus on 2007-08-13
> **Happy_Man said:**
>  ```
sudo mkdir /media/ntfs
sudo mount /dev/sda<partition number> /media/ntfs
```

IIRC, the filesystem needs to be specified.

So perhaps this will work:

```

sudo mount dev/sda<partition number> /media/ntfs [SIZE=-1] -t ntfs -o nls=utf8,umask=0222
[/SIZE]
```[SIZE=-1]
If this works, you then can add a line to /etc/fstab so it will be permanent.

-merlin
[/SIZE]

---

### Post by Atrio05 on 2007-08-14
it's an external usb drive so is it still ok to do it the way you specified?

---

### Post by Atrio05 on 2007-08-14
ok still doesn't mount and now i get this error :


[I]An error occurred while enabling /media/ntfs.
The system reported: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so[/I]

so yea i really need to get this drive m,ounted it contains all my data from my previous install (ubuntu dapper) and i would just really enjoy using kubuntu a whole lot more if it would work better with my drive!!

thanx!

---

### Post by Happy_Man on 2007-08-15
Ah, so this was an ext3 filesystem on the drive? Then, use this command: ```
sudo mkdir /media/test
sudo mount -t ext3 dev/sdb1 /media/test
```

---

