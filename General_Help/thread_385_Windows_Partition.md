---
title: "Windows Partition"
date: 2004-10-13
forum: General Help
---

### Post by hugo on 2004-10-13
I am having trouble with my windows partition, I mounted it by writing the following in the fstab file: /dev/hda1    /media/windows    vfat    auto,user,rw   0  0

My problem is it used to work but now when I access it shows the files and folders as gnome icons (paper with foot on), when I click on them notthing happens and when I right click on it, the icons dissapears.

When I try to access it in the terminal, it tells me I do not have permission. If I sudo -s it works, I can write to it and read from it.

Is my problem permission related? I want to be able to do that graphically though, and it does not want to work.

What to do?

Thanks

---

### Post by flygmaskin on 2004-10-13
It sounds like you have the wrong permissions set. Try opening up a terminal and run "sudo chmod -R 755 /media/windows"

---

### Post by hugo on 2004-10-13
I tried that, it does not want to work, in terminal I get "Permission Denied" and in Gnome I still get the Gnome Icons.

This distro really kicks butt, but I just wish I can get this sorted out with some help.

Thanks for the response flygmaskin

---

### Post by Rancoras on 2004-10-13
Here's my line for a FAT32 partition:

```
/dev/hdb2    /media/backup    vfat    rw,uid=1000,gid=1000   0   0
```

Cheers

---

### Post by FLeiXiuS on 2004-10-13
Well first off, the user parameter is incomplete.  I would go about adding something like this and include a uid / gid.  

FSTAB
```
/dev/hda1 /media/windows vfat auto,uid=$uid,gid=$gid,rw 0 0
```

I would set the UID to your default users ID #.  
```
$EDITOR /etc/passwd
```
for more info.

This correctly mounted my vfat partitions / hard drives.

The GID is optional.  If your default user has a group then set its GID.  You can determine its ID by editing:
```
 $EDITOR /etc/groups
```

If this doesn't do it for you, then please post any error messages.

Other things to keep in mind.  Make sure your windows partition is vfat / hda1.  Just a check some of us intelligent people forget :-).

---

### Post by BIN.anomaly on 2004-10-13
I've the same problem with my NTFS partitions. I've set it up in fstab and I can browse them using terminal (after I've change my status to SU), but when i'm tryin to use them by default file manager...it doesn't works. System displays me that I don't  have permission to browse those partitions.
Firstly i thought that UBUNTu doesn't support NTFS file systems, but when I saw, that I can enter to  Windows partitions by terminal - I've changed my mind.
I've took example of Rancoras, and try to rewrite to my fstab (I've the same UID and GID like him, so needn't change much- i've checked it in my group/user managrer) but the same information is popin up when I want to brows my disks. :(

---

### Post by BIN.anomaly on 2004-10-13
Ok, I've done it :)
I've added   umask=002   to my fstab and now it works properly. 
sorry for botherin y'all

---

### Post by oddabe19 on 2004-10-13
So, wait... is it no longer /mnt with 2.8? or is it /media??
Cause my fstab goes 
```
/dev/hdb1    /mnt/stuff    vfat    rw,users,umask=0000   0   0
```
and I get that same problem.... even when i created the 'stuff' folder, i did a 'sudo chmod 777 /mnt/stuff' and a 'sudo chown oddabel /mnt/stuff'

I get the same problems as reported before....

Also, i don't see a grub.conf.... how can I change the OS list time from 1 sec to like 10? :x [/code]

---

### Post by FLeiXiuS on 2004-10-13
Yes its /media now :-).

Grub config is located in /boot/grub/menu.lst

---

### Post by hugo on 2004-10-14
Thanks to all of you, I am sorted out, and a very happy chappie  :D

---

