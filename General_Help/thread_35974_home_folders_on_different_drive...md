---
title: "home folders on different drive.."
date: 2005-05-21
forum: General Help
---

### Post by CrustyDOD on 2005-05-21
hey

i have server version of Ubuntu installed on my 1.1GB drive :)
and i have another disk in pc that is empty and its a bit bigger! So how do i move/transfer /home folders to that drive? I also want that is user loggs in over FTP or SSH, he goes that the home folder on that second drive..

All help wanted...

---

### Post by f.prisson on 2005-05-21
I would do the following:

1. Move the content of the current /home folder to a temp directory.
2. Create a partition on the second disk, format it with a filesystem of your choice
3. Edit /etc/fstab, so that the partition is mounted at boot up as /home
4. Mount it manually the first time on /home
5. Copy all user folders from the temp directory to /home. Take care of the ownership and permissions of the data

---

### Post by CrustyDOD on 2005-05-21
[QUOTE=f.prisson]I would do the following:

1. Move the content of the current /home folder to a temp directory.
[/QUOTE]
Move to /usr/home

[QUOTE=f.prisson]
2. Create a partition on the second disk, format it with a filesystem of your choice
[/QUOTE]
Its hdc1 - ext3

[QUOTE=f.prisson]
3. Edit /etc/fstab, so that the partition is mounted at boot up as /home
[/QUOTE]
did it like this:
/dev/hdc1       /home           ext3    defaults        0       0

[QUOTE=f.prisson]
4. Mount it manually the first time on /home
[/QUOTE]
Did it like:
sudo mount /dev/hdc1 /usr/home

Now i think this is kinda wrong.. so how on earth do you mount a hdc1 partition? I know how to mount windows fat32 one and i bet its not the same so i won't even try it :)

Basically, i'm lost at point 4 :(

And when you do finally mount it how do you access it? I'm doing this in console! connected to server over ssh.. Just cd /home?

---

### Post by f.prisson on 2005-05-21
```
/dev/hdc1 /home ext3 defaults 0 0
``` you still have to add an auto here, or you have to mount it manually on each reboot

```
sudo mount /dev/hdc1 /usr/home
``` Thats wrong. The correct command is```
sudo mount /home
``` if your /etc/fstab is edited right,without you do it with ```
sudo mount -t ext3 /dev/hdc1 /home
``` Now you can copy your user data from /usr/home to /home.

At his point everything is as before, the data is still in /home but is located on an other physical disk.

---

### Post by CrustyDOD on 2005-05-21
ok so i added auto to fstab:

```

/dev/hdc1       /home           ext3    defaults,auto   0       0

```

rebooted
copied /usr/home to /home and it works..

thx!

---

