---
title: "Permission problems"
date: 2008-01-29
forum: General Help
---

### Post by litium on 2008-01-29
I moved my /home to a disk partition, separated from root using the following these steps (under a no graphic session)

1- sudo mkdir /mnt/myhome

2-sudo mount /dev/hda9 /mnt/myhome

3-sudo mv /home/* /mnt/myhome/

4-sudo gedit /etc/fstab

5 /dev/hda6 /home ntfs defaults,errors=umount-ro 0 1

8.-Delethe the  /myhome folder from /mnt

9.- Reboot.

It worked really swell, but when i moved the home folder i must messed up using sudo, because now evirtying is only root root (viewing permissions whit ls -l).

I tried changin the permissions whit chmod, and the other command that uses -r user:group path. Nothing will change. A little help would be aprecciated. I'm using 7.10
And when i login, for example it says tahta .drnc or somthing needs 644 for permission or something like that.

---

### Post by bodhi.zazen on 2008-01-29
Well, the error was using sudo to move the contents of home, and possible with the permissions of the destination ...

FYI, to move /home :

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by litium on 2008-01-29
Thanks, but now home is alredy moved and the permissions changed. How do i set them back to me? instead of root:root they should be litium:litium (at least /home/litium)

I tried all the commands to change the permissions, non worked. Using sudo, and even a Root terminal.

---

### Post by bodhi.zazen on 2008-01-29
did you move your /home to a FAT or NTFS partition ? (that would be my guess).

---

### Post by litium on 2008-01-29
> **bodhi.zazen said:**
> did you move your /home to a FAT or NTFS partition ? (that would be my guess).

Yeap. To an NTFS paritition. I tried running *gksudo nautilus* to change the permission, but it won let me.

---

### Post by bodhi.zazen on 2008-01-29
Ownership and permissions of NTFS and FAT partitions are set at the time of mount. NTFS and FAT do NOT support permissions, so I advise you move /home yet again to ext3 (or other linux native file system).

For reference : _Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

### Post by aysiu on 2008-01-29
I don't think /home can operate properly on an NTFS or FAT partition.

---

### Post by litium on 2008-01-29
Many thanks for the reply! So, now, wich steps should i take to move /home to / again. So i can format the NTFS partition to ext3.

I can boot whit the LiveCD, copy all HDC9 contents to a tempal directory, format HDC9 to EXT3, Move all data from the temp dir, edit FSTAB and reboot?. Will it work?

Thanks

---

### Post by bodhi.zazen on 2008-01-29
I advise you boot to recovery mode, back up your data from your old home (you can copy it to /root)

Then format and mount your new /home partition, update /etc/fstab. Then make a user, be sure to add the new user to the admin group (at least). Then copy your old data to your new home.

The problem is you did not follow the standard procedure to copy /home and you copied to a ntfs partition, so permissions may be quite problematic.

See : [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

for a more detailed how and why.

---

### Post by litium on 2008-01-29
I've backed my data... but i'm not sure how to format /home if it is in use...

EDIT: YAHOOOOOOOOO!

I boot the liveCD, copied litium to /root, formated HDc9 to ext3, modifieded fstab and rebooted. OH NOES! My gnome session wont start?! WHY? Don't care... Gnome Session Fail Safe... enter my deskpot as i remembered!!! Well, let's log out. Now, GNOME SESSION. IT ENTERED! So happy! :guitar:

---

