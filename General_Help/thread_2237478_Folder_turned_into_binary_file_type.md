---
title: "Folder turned into binary file type"
date: 2014-08-02
forum: General Help
---

### Post by zane3 on 2014-08-02
Somehow my movie and TV Show folder was turned into a "binary file". It does not look like the files were deleted as the hard drive is still as full as it was before these binary files replaced the folder. When I click on the binary file I'm presented with a error message saying I don't have permissions. This is odd because when I check the permissions on the folder it says I am the owner.  I have added some screenshots and would appreciate any help. Thank you in advance. 














[IMG]http://i.imgur.com/rFoLKI1.png[/IMG]                    [IMG]http://i.imgur.com/SHHyhLn.png[/IMG]                               [IMG]http://i.imgur.com/0xmSYwv.png[/IMG]

---

### Post by ajgreeny on 2014-08-02
You may get more info from the command ```
ls -l Movies
```
This assumes that the Movies folder is in your home.

---

### Post by Impavidus on 2014-08-02
The Movies directory seems to be in /media/zane/Media1. This would make the command```
ls -l /media/zane/Media1
```I assume the movies are on a separate partition or external drive that is mounted automatically (but not at boot). So, can you tell whether it is external or an internal drive, what kind of partition this is and whether you use encryption. And because we may need additional information, also run these commands:```
mount
sudo blkid
```

---

### Post by ajgreeny on 2014-08-02
Sorry I didn't notice the pathways to that folder.
Actually the command would be ```
ls -l /media/zane/Media1/Movies
``` for that Movies folder.

---

### Post by zane3 on 2014-08-02
[COLOR=#000000]When executing ls -l: [/COLOR] 

[COLOR=#000000][FONT=Arial]zane@Server:~$ sudo ls -l /media/zane/Media1/Movies[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][sudo] password for zane:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]total 1388[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Oct  8  2012 127 Hours (2010)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Feb 20 11:54 12 Years a Slave (2013)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Mar 27 20:46 2001 A Space Odyssey[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Mar 11 19:21 500 Days of Summer[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Oct 20  2012 50 50 (2011)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Jan  5  2014 About Time (2013)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Jan 13  2013 A Christmas Story (1983)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 May 20 10:53 Adaptation (2002)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Mar 13 18:09 A History of Violence (2005)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Jan 29  2014 All Is Lost (2013)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Dec 22  2013 Amélie (2001)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane plex 4096 Oct  6  2013 American Beauty (1999)[/FONT][/COLOR]
[COLOR=#000000]**etc. just continues to list my movies like this**


[FONT=Verdana]When executing mount:
[/FONT]
[FONT=Arial]zane@Server:~$ mount[/FONT]
[FONT=Arial]/dev/sdb1 on / type ext4 (rw,errors=remount-ro)[/FONT]
[FONT=Arial]proc on /proc type proc (rw,noexec,nosuid,nodev)[/FONT]
[FONT=Arial]sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)[/FONT]
[FONT=Arial]none on /sys/fs/cgroup type tmpfs (rw)[/FONT]
[FONT=Arial]none on /sys/fs/fuse/connections type fusectl (rw)[/FONT]
[FONT=Arial]none on /sys/kernel/debug type debugfs (rw)[/FONT]
[FONT=Arial]none on /sys/kernel/security type securityfs (rw)[/FONT]
[FONT=Arial]udev on /dev type devtmpfs (rw,mode=0755)[/FONT]
[FONT=Arial]devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)[/FONT]
[FONT=Arial]tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)[/FONT]
[FONT=Arial]none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)[/FONT]
[FONT=Arial]none on /run/shm type tmpfs (rw,nosuid,nodev)[/FONT]
[FONT=Arial]none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)[/FONT]
[FONT=Arial]none on /sys/fs/pstore type pstore (rw)[/FONT]
[FONT=Arial]/dev/sda1 on /media/zane/Media1 type ext4 (rw)[/FONT]
[FONT=Arial]/dev/sdc1 on /media/zane/Media2 type ext4 (rw)[/FONT]
[FONT=Arial]systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)[/FONT]
[FONT=Arial]gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=zane)[/FONT]




[FONT=Verdana]When executing[/FONT][FONT=Verdana] blkid: 

[/FONT][FONT=Arial]zane@Server:~$ sudo blkid[/FONT]
[FONT=Arial]/dev/sda1: LABEL="Media1" UUID="4349774e-a79c-4f56-a50b-40ebef3987a6" TYPE="ext4"[/FONT]
[FONT=Arial]/dev/sdb1: UUID="415b6b5a-587e-428d-821f-1910a17d5a28" TYPE="ext4"[/FONT]
[FONT=Arial]/dev/sdb5: UUID="af0c07f1-3562-4b73-94a1-86743daf5ac4" TYPE="swap"[/FONT]
[FONT=Arial]/dev/sdc1: LABEL="Media2" UUID="23e03c4e-aac9-4a81-9f25-c90ad82326a2" TYPE="ext4"[/FONT]


[FONT=Arial]This is on another internal hard drive and not in my home folder. The hard drive I'm experiencing this on it mounted in sda1 and it does mount on boot. [/FONT][/COLOR]

---

### Post by ajgreeny on 2014-08-02
My only query is why you get the **zane [COLOR=#ff0000]plex[/COLOR]** in each file listing for ownership instead of what I expect which is **zane zane**.  Are you using a plex media server?
```

[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane [/FONT][/COLOR][COLOR=#ff0000][FONT=Arial]plex[/FONT][/COLOR][COLOR=#000000][FONT=Arial] 4096 Feb 20 11:54 12 Years a Slave (2013)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane [/FONT][/COLOR][COLOR=#ff0000][FONT=Arial]plex[/FONT][/COLOR][COLOR=#000000][FONT=Arial] 4096 Mar 27 20:46 2001 A Space Odyssey[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drw-rw-r-- 2 zane [/FONT][/COLOR][COLOR=#ff0000][FONT=Arial]plex[/FONT][/COLOR][COLOR=#000000][FONT=Arial] 4096 Mar 11 19:21 500 Days of Summer[/FONT][/COLOR]
```

---

### Post by steeldriver on 2014-08-02
... also they appear to be **directories** but they don't have **execute** permission (for anybody) - so you won't be able to open them to see any files inside

---

### Post by zane3 on 2014-08-02
I am using Plex Media Server with these files.

---

### Post by zane3 on 2014-08-02
Could you tell me how to change them so I can open them and see the files inside?

---

### Post by ajgreeny on 2014-08-03
You can use the **chmod** command.
I think something like ```
chmod +x /media/zane/Media1/Movies/*
``` should do it, assuming you have permission to write to that folder.

---

### Post by zane3 on 2014-08-04
That didn't do the trick. Even after reinstalling I am able to open the folders but unable to see anything inside of them. I have a feeling that this is a lost cause and I'm better of just formatting the drive and starting over.

Thank you for all your help.

---

