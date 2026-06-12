---
title: "Trying To Change Home Partition"
date: 2008-06-27
forum: General Help
---

### Post by Brando569 on 2008-06-27
I have /home and / as two different partitions, I'm trying to make /home exist on the same partition as / (like it normally is). I copied everything from /home (/dev/sda4) to /home1 (/dev/sda3), logged out and went to a terminal logged in as root, unmounted /dev/sda4 changed the device to /dev/sd3, renamed /home1 to /home, and remounted /home. 

I went back to KDM expecting everything to work and typed in my password, it flickered for a second then brought me back to the login screen. I tried to login as myself via another terminal (tty3) and it worked without a hitch. I restarted X via ctrl+alt+backspace and tried it again, same thing. I went back to the root terminal and stopped and restarted KDM, same thing. I rebooted the computer, same thing. I finally ran out of ideas and changed /dev/sda3 back to /dev/sda4, logged in and everything went as it should.

Is there something in the xserver that tells it to look for my /home in /dev/sda4 and not anyplace else??

---

### Post by unutbu on 2008-06-27
Please post

```
cat /etc/fstab
```

---

### Post by Brando569 on 2008-06-27
this is how it is now (and how it was when i initially installed it):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>                     <dump>  <pass>
proc            /proc           proc            defaults                        0       0
/dev/sda3       /               ext3            defaults,errors=remount-ro      0       1
/dev/sda4       /home           ext3            defaults                        0       2
/dev/sda1       /media/windows  ntfs            defaults,umask=007,gid=46       0       1
/dev/sda5       /media/stuff    ntfs            defaults,umask=007,gid=46       0       1
/dev/sdb1       /media/media    ntfs            defaults,umask=007,gid=46       0       1
/dev/sdb2        none           swap            sw                              0       0
/dev/sdc1       /media/mybook   ntfs            user,noauto,exec                0       1
/dev/scd0       /media/cdrom1   udf,iso9660     user,noauto,exec                0       0

```


this is what it looked like when kdm wouldnt let me login, yet i could do it via the console:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>                     <dump>  <pass>
proc            /proc           proc            defaults                        0       0
/dev/sda3       /               ext3            defaults,errors=remount-ro      0       1
/dev/sda3       /home           ext3            defaults                        0       2
/dev/sda1       /media/windows  ntfs            defaults,umask=007,gid=46       0       1
/dev/sda5       /media/stuff    ntfs            defaults,umask=007,gid=46       0       1
/dev/sdb1       /media/media    ntfs            defaults,umask=007,gid=46       0       1
/dev/sdb2        none           swap            sw                              0       0
/dev/sdc1       /media/mybook   ntfs            user,noauto,exec                0       1
/dev/scd0       /media/cdrom1   udf,iso9660     user,noauto,exec                0       0

```

---

### Post by unutbu on 2008-06-27
Comment out this line from /etc/fstab:
```
**#**/dev/sda3       /home           ext3            defaults                        0       2
```

/dev/sda3 is mounted at / in the line that precedes it. You do not want to also mount the same /dev/sda3 at /home.

---

### Post by Brando569 on 2008-06-27
duh! *smacks self on forehead* and i make another stupid mistake lol, thanks.

edit:i also had to take ownership of all the stuff inside /home/bran since it was owned by root.

---

