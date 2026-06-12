---
title: "Moving Ubuntu installed on extended partition to primary partition"
date: 2016-03-27
forum: General Help
---

### Post by ubuserone on 2016-03-27
New to ubuntu.I had install 14.04 LTS on an extended partition 40GB but after years for usage , I plan to move it to a primary partition which is larger partition.
How do I do that ? any guide moving an OS installed without losing any files ?

---

### Post by yancek on 2016-03-27
It is possible but if you don't have experience/knowledge of it you will likely have a lot of problems.  There are a number of different methods of copying and you can save owner:group and permissions.  The problems you will have is that you will have a new UUID as it will be a different partition and your /etc/fstab and all your boot files will also be ina different location so you will need a Live CD/DVD or flash drive of Ubuntu or another Linux to correct these.

You might wait until next month and download and install version 16.04 on the other partition and then copy your data to it.

---

### Post by ubuserone on 2016-03-29
> **yancek said:**
> It is possible but if you don't have experience/knowledge of it you will likely have a lot of problems.  There are a number of different methods of copying and you can save owner:group and permissions.  The problems you will have is that you will have a new UUID as it will be a different partition and your /etc/fstab and all your boot files will also be ina different location so you will need a Live CD/DVD or flash drive of Ubuntu or another Linux to correct these.

You might wait until next month and download and install version 16.05 on the other partition and then copy your data to it.
So , do you have a guide for it ? I plan to test out to know whether it works to get more space.

16.05 , Even coping the data , I still need to reinstall all the application from start to end again.Does moving data can prevent to get application reinstall on 16.05 ?

---

### Post by yancek on 2016-03-29
If you have a lot of data, you could create another primary partition or use a current primary and copy data such as movies, music or whatever you have to that partition.  If you have a lot of software installed that needs to be on the / partition, that probably won't work.  The Ubuntu site is the official documentation.  You might read through it to get an idea of how it works in general.

 [https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)

---

### Post by oldfred on 2016-03-29
Your normal backup should also include a list of installed applications.
And your /home has all the settings/configurations in hidden files for all those applications.

Do you now have separate /home? And/or data partition.
I suggest new users use default of / & swap. Then then next somewhat more advanced suggestion is separate partition for /home. 
And then keep /home inside / (root) like default install, but have all data in data partition. requires some understanding of partitions, ownership & permissions linking.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 
            Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559) 
    
If you just want to move /home to new partition:
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving


[/URL]

---

### Post by Bucky Ball on 2016-03-29
14.04 LTS upgrades directly to 16.04 LTS via the net. You don't have to reinstall all apps doing it that way. Why not just expand the extended partition or that is not possible?

---

### Post by PaulBx on 2016-03-29
> I had install 14.04 LTS on an extended partition 40GB 

40GB is awfully large. Are you sure there is not some extraneous garbage in there that cannot be removed, or some directories that cannot be copied to another mounted partition with stuff like jpegs?

To find the garbage, I like gdmap. I just used it recently to find a bunch of old kernel module directories that took up huge amounts of disk space.

Running in 40GB should be easy. Using an extended partition should not be a problem.

Thanks oldfred for that link on moving /home, that will be useful to me.

---

