---
title: "[SOLVED] Help Cannot remove spyware in windows xp"
date: 2008-06-10
forum: General Help
---

### Post by abh83 on 2008-06-10
My father who uses Windows XP Pro SP2 somehow managed to install the Spyware parasite known as Antivirus 2008.

I've tried several application but non of them manage to detect or remove it.

I've used AVG Free, Lavasoft Adaware 2008 Free, Spybot - Search and Destroy. I also tried using Spyware Doctor and SpyHunter but they only scan your computer for free, in order to remove the spyware one must register and buy the product.

Help is greatly appreciated!

(one of the main reason why I moved to Ubuntu)

---

### Post by TeoBigusGeekus on 2008-06-10
[http://www.xp-vista.com/spyware-removal/antivirus2008-antivirus-2008-removal-instructions]("http://www.xp-vista.com/spyware-removal/antivirus2008-antivirus-2008-removal-instructions")

---

### Post by mikewhatever on 2008-06-10
I hope General Help section is not turning into Windows spyware removal and what not support thing. You might want to bookmark the section for Windows, for your father.
[Windows Discussion]("http://ubuntuforums.org/forumdisplay.php?f=170")

---

### Post by kayslay on 2008-06-10
****visit [www.malwarebytes.org](www.malwarebytes.org) and download their latest spyware removal tool,its free,scan yur computer after installing it and see for yurself:guitar:

---

### Post by abh83 on 2008-06-10
Thx for the responses. Sorry for posting this in the wrong forum but I am stressed out and under time  pressure. My dad has some important office files and documents.

Anyway, I have followed the link posted above but I seem to have moved the wrong .dll shell files and now I cannot login to windows anymore. So I popped in the live cd and I am trying to mount the windows harddisk but since it was not unmounted properly Ubuntu (live cd) cannot mount windows harddisk.

I will have to force mount the windows harddisk myself but i need root privileges in ubuntu live cd.

what would the password be?

---

### Post by abh83 on 2008-06-10
okay so its sudo su -

```
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ed261ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+   7  HPFS/NTFS
root@ubuntu:~# 
```

how do i mount my harddisk?

---

### Post by abh83 on 2008-06-10
> root@ubuntu:~# mount -t ntfs-3g /dev/sda1 media/disk -o force
fuse: failed to access mountpoint media/disk: No such file or directory
root@ubuntu:~# mount -t ntfs-3g /dev/sdb1 media/disk -o force
fuse: failed to access mountpoint media/disk: No such file or directory
root@ubuntu:~# 


what am i doing wrong?

---

### Post by bollix47 on 2008-06-10
You forgot the / in front of media?

---

### Post by abh83 on 2008-06-10
fuse: failed to access mountpoint /media/disk: No such file or directory


nope

---

### Post by bollix47 on 2008-06-10
Did you create that directory?

```
sudo mkdir /media/disk
```

---

### Post by abh83 on 2008-06-10
Thx dude!!! I forgot to create that directory. I thought it would create automatically.

Finally problem solved!

---

