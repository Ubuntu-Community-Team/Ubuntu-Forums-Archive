---
title: "chmod and chown to allow file/folder access to several users"
date: 2013-05-02
forum: General Help
---

### Post by ivotkl on 2013-05-02
Hello. I have decided to play around with tty(s) linux has and I have created 2 new users.


One that will be in charge of media playing (permission granted was standard user) and the other one that will be an administrator in charge of backing-up the system. Physically, all 3 users would be me. I'm just trying to learn a bit about this to be able to apply it in a couple of years at a job.


For the purpose of this thread, let's call them like this:
ivan: original account created when system was installed (System Administrator).
ivan-media: intended for media playing (Standard User).
ivan-backup: support / backup (System Administrator). 


Current situation is as follows:
I have a NTFS partition used for Backups and I'm trying to change the permissions on the whole logical disk to be 755, so that owner (user1) can have full access to the file/s and the other users of the machine can at least list and read files.


I have tried the following logged in as user1:


```
$sudo chown -v ivan /media/506C1EA132F525C2
[sudo] password for ivan: 
ownership of `/media/506C1EA132F525C2' retained as ivan
$ sudo chmod -Rv 744 /media/506C1EA132F525C2
```


(Above command results ommited as it was too large to display)


Result was that files permissions were changed from 0600 (rw-------) to 0744 (rwxr--r--).


However:
```
$ls -l
drwx------ 1 ivan ivan 4096 May  1 08:38 506C1EA132F525C2
```


Similar thing happened to its content.


Any ideas?


Thank you in advanced. =)


***EDIT:*** I've tried what was suggested [here]("http://forums.debian.net/viewtopic.php?f=10&t=13033&p=493173&hilit=chmod#p493173"), but nothing has changed. Apparently it kicks me out (Error was Permission denied or similar, I don't recall exactly). Apparently it kicks me out (Error was Permission denied or similar, I don't recall exactly). Permissions remain unaltered.

---

### Post by Impavidus on 2013-05-02
Permissions and owner on NTFS partitions have to be set using the mount options. NTFS does not know about Linux permissions.

How do you make your backups? If you're just copying (suggested as you say there are a lot of files) to that NTFS partition then information on owner and permissions is lost, which is not good for full system backups.

---

### Post by Morbius1 on 2013-05-02
***Unmount the partition if it is currently mounted:***
```
sudo umount /media/506C1EA132F525C2
```
***Create a home for the partition to Live in:***
```
sudo mkdir /media/Shared
```
***Add the following line to the end of /etc/fstab***
```
UUID=506C1EA132F525C2 /media/Shared ntfs defaults,nls=utf8,uid=1000,umask=0022,windows_names 0 0
```
***Then run the following command to test for syntax errors and if there are none mount the partition:***
```
sudo mount -a
```

That should give you a mounted partition with 755 permissions but it will not fulfill your original requirement:
> For the purpose of this thread, let's call them like this:
ivan: original account created when system was installed (System Administrator).
ivan-media: intended for media playing (Standard User).
ivan-backup: support / backup (System Administrator). 

***If you still want that to happen then create a new group, let's call it "special":***
```
sudo groupadd special
```
***Then add both ivan and ivan-backup to that group:***
```
sudo gpasswd -a ivan special
sudo gpasswd -a ivan-backup special
```
[COLOR=#0000cd]*Note: you will have to logout and log back in to have those group memberships registered.*[/COLOR]
***Then change the fstab entry to this:***
```
UUID=506C1EA132F525C2 /media/Shared ntfs defaults,nls=utf8,uid=1000,gid=special,umask=0002,windows_names 0 0 
```
That will produce a mounted partition with the following permissions:
owner = ivan
group = special
permissions = 775

** NTFS was not the best filesystem to experiment with chmod / chown since it has no affect on ntfs as          Impavidus stated above.
** And as Impavidus also stated you will loose all of the original owner / permissions of the backup when it's placed in an ntfs partition unless you are compressing it say in a tar or zip format.

---

