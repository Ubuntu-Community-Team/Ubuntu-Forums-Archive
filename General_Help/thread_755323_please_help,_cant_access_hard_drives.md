---
title: "please help, cant access hard drives"
date: 2008-04-14
forum: General Help
---

### Post by mastercheif2253 on 2008-04-14
hello, i am having problems accessing windows hard drives, im new to any linux system, its just that this current computer im using isnt good enough to use xp, so i switched and now i cannot access all my data please help

---

### Post by bodhi.zazen on 2008-04-14
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

### Post by mastercheif2253 on 2008-04-14
well, i have ntfs hard drives, and i used the ntfs tool to mount them, but now when i click on the drives to access them, it says you do not have the privledge to mount this drive, please help

---

### Post by bodhi.zazen on 2008-04-14
If you are asking about ntfs-config, the tool needs to be run as root :

```
gksu ntfs-config
```

If you are asking about mounting the drive

```
sudo fdisk -l
``` to list your partitions.

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sdxy /media/windows -o uid=1000,gid=100,umask=007
```

where "sdxy" = your windows partition.

If you like that add an entry in fstab

```
gksu gedit /etc/fstab
```

> /dev/sdxy /media/windows  ntfs-3g  uid=1000,gid=100,umask=007 0 2

---

### Post by mastercheif2253 on 2008-04-14
ok, all i know is that when i go to computer and i try to access one of my hard drives i put in, it says Cannot mount volume. You are not privileged to mount the volume,

---

### Post by bodhi.zazen on 2008-04-14
What happened when you inputed the commands I gave you ?

---

### Post by mastercheif2253 on 2008-04-14
when i went to open ntfs tools, it doesnt list my drives to mount

---

### Post by bodhi.zazen on 2008-04-14
What about the other commands I gave you ?

---

### Post by ajmorris on 2008-04-14
hi there,
you mean when you click on your drive, and it says it cant mount it, that is in nautilus? (the default gnome Graphical file manager)

if so, you need to run nautilus as root if that is how you are mounting the drive, you can edit your /etc/fstab, in the way bodhi.zazen has described, and add the option 'users' to make it so all users can mount it.
Hope that sorta helps,

IMHO, you are better off using the commands bodhi outlined to mount the drive however.

AJ

---

### Post by mastercheif2253 on 2008-04-14
i got to the part where you type sudo mount -t ntfs-3g /dev/sdxy /media/windows -o uid=1000,gid=100,umask=007 and it comes up saying Mount is denied because NTFS is marked to be in use. Choose one action: and i chose mount -t ntfs-3g /dev/sdd1 /media/windows -o force
and it says it has to be run from root

---

### Post by ajmorris on 2008-04-14
> **mastercheif2253 said:**
> i got to the part where you type sudo mount -t ntfs-3g /dev/sdxy /media/windows -o uid=1000,gid=100,umask=007 and it comes up saying Mount is denied because NTFS is marked to be in use. Choose one action: and i chose mount -t ntfs-3g /dev/sdd1 /media/windows -o force
and it says it has to be run from root

When you run the action that you chose (mount -t ntfs-3g /dev/sdd1 /media/windows -o force) put a 'sudo' out the front, so it is:
```

sudo mount -t ntfs-3g /dev/sdd1 /media/windows -o force
```

---

### Post by mastercheif2253 on 2008-04-14
thats what the problem was, thanks so much, now i can listen to my terabyte of music i have, lol

---

