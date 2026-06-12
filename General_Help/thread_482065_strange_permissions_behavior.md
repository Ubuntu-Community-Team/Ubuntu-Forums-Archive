---
title: "strange permissions behavior"
date: 2007-06-23
forum: General Help
---

### Post by rolfbeethoven on 2007-06-23
I'm seeing some permissions behavior that I don't understand.  I created a folder as root, but chown'd it to my user account and group.  I also chmod'd it to 777.  The same with the parent directory.

When I try to 'ls -l' as the user, I get '?---------- ? ? ? ?'.  When I 'sudo ls -l', I can see the correct data.  Why do I need to act as root to see this information since I own everything and have read access?

I'm working on a box that had Win XP installed and I put Ubuntu Feisty on top of it.

Thanks.


*******************************************************
Here is the output from my terminal...

tyler@mythbox:~$ ls -l /storage/fileserver/tyler
total 0
?--------- ? ? ? ?                ? /storage/fileserver/tyler/testfile.txt

tyler@mythbox:~$ sudo ls -l /storage/fileserver/tyler
Password:
total 180
-rwxrwxrwx 1 root  root  64408 2007-06-22 07:01 testfile.txt

tyler@mythbox:~$ sudo ls -l /storage/fileserver/
total 28
drw-rw-rw- 2 tyler tyler 4096 2007-06-23 00:08 tyler

tyler@mythbox:~$ sudo ls -l /storage
total 3351416
-rw-r--r--  1 root     root     3428458299 2007-06-20 22:09 backup.img.gz
drwxrwxrwx  8 tyler    tyler          4096 2007-06-23 00:05 fileserver
drwxrwxrwx 94 www-data www-data       4096 2007-06-14 22:51 music
drwxrwxrwx  2 www-data www-data       4096 2007-06-21 06:48 recordings
drwxrwxrwx 10 www-data www-data       4096 2007-06-22 23:56 video
tyler@mythbox:~$


tyler@mythbox:~$ fdisk -l
tyler@mythbox:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/sda2            1217        2432     9767520   83  Linux
/dev/sda3            2433        2557     1004062+  82  Linux swap / Solaris
/dev/sda4            2558       24321   174819330   83  Linux
tyler@mythbox:~$

*******************************************************

---

### Post by rolfbeethoven on 2007-06-23
I resolved the problem, but I would still appreciate it, if someone could explain to me why it wasn't working before.  I'll explain.

I created the directories as root (sudo mkdir ...).  I chown'd the directory back to user:user and chmod'd it to 777.  The new settings showed up, however, I knew something was wrong because I didn't have real control over them as I wrote in the first post.

The solution was to 'su -' to root and then chown the directory.  Now I can access them normally as user.

This may be a good tip, if you didn't know already.  In this case, the 'sudo' command didn't really get the job done.  I needed to be logged in as root.  Can someone explain to me why this is the case?

---

### Post by mustali on 2007-06-23
The permissions on the 'tyler' folder are correct but the files within it did not get the permissions set probably because you applied chmod to 'tyler'. This will leave the permissions of the files within that folder intact. To change the permissions of a folder and its contents use 
```

cd /storage/fileserver
chmod -R  777 tyler

```

or 
```

cd /storage/fileserver
chown -R tyler:tyler tyler

```

HTH

---

