---
title: "data partition"
date: 2013-06-29
forum: General Help
---

### Post by thorbs on 2013-06-29
Some time ago I read an article on this forum about making a data partition, which I decided to do. I got around to do it the other day, but for some reason I am not able to access or save on that partition. 
I have been searching for the thread I read without luck. So if somebody know the thread I am talking about and could direct me to it, I would be gratefull. Alternatively if anybody knows what could hinder access to a newly created data partition, that would be great as well. 


thanks

---

### Post by decrepit on 2013-06-29
Having the wrong permissions is the prime suspect.
Have you mounted it ok?
If so try 
> gksudo nautilus

Then navigate to where you've mounted it and see if you can access it as "root". If you can, right click on the partition and select properties, permissions. You should then be able to change the permission to user, read write.
If that doesn't work you can do it from the command line, I can't quite remember  how, look up chmod.

---

### Post by oldfred on 2013-06-29
Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Best to automount in fstab, but you can manually mouht it and set ownership & permissions.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by Bashing-om on 2013-06-29
decrepit; Hi 

Accessing that data partition should be no big deal ... as advised ,, check permissions.
1. Does the partition exist ?
```
 sudo fdisk -lu
```
2. Is there a mount point established ?
```
ls -la /media/
ls -la /mnt/
ls -la /media/user-name/
```where user-name is your actual "user_name"
3. Can you mount that partition manually from the terminal ( need the mount point to see).
a) are you wanting it to auto mount the partition on boot up ?
b) Is the partition to be mounted on-demand ? 

[INDENT][INDENT]we will see what is to be seen[/INDENT][/INDENT]

---

