---
title: "Hd1 Ubuntu, Hd2 Windows. Problems accessing Ubuntu."
date: 2015-11-21
forum: General Help
---

### Post by kvanoff on 2015-11-21
Hi all, this is my first post, or my second one. ill discover that.  So, i got this pc with two hard disk. One with Ubuntu, One with Windows. My  problem with the first hard disk with ubuntu is that i can t walk out  from a login screen loop; this is the hard disk where i stocked all my  files. I tried to create a new user and its the same for it, qnd either  for guest session. I also researched a little on the internet for some  solution and tried with no success those commands at the "urgency"  terminal (ctrl-alt-f1)(from which i can login into the system):
 > sudo startx sudo dpkg-reconfigure xserver-xorg sudo dpkg-reconfigure lightdm sudo rm .Xauthority   also i tried to update and upgrade. So, is there something you know i  can try to access to my old ubuntu, where all my files are?  

And also some auestions to try to understand how i can save my files on hd1ubuntu, and to have a unique ubuntu system with two hard drives. Im sorry for my english, ill do better, what is important that you understand is that first of all i have absolutely to save my files, and then i want to "merge" the two hd in one system only, with a unique copy of ubuntu on my pc's system.
So, who s going to help me defeating the monster? 

Thanks

---

### Post by oldfred on 2015-11-21
Windows will not read Linux partitions, but Ubuntu will mount and let you use NTFS partitions. But if planning on not using Windows best not to use NTFS as it needs chkdsk periodically and you can only run that from Windows.

Are you having two issues? Better to have each question as a separate thread with a good title to attract users knowledgeable on that issue.

Are issues Logging in & mounting data partitions?

Each user has his own /home and other users cannot access that users data. You need to log in with the initial user you created when you installed system. That user is the only one that can use sudo to temporarily be the admin and do system tasks.

Post this from either a working install or the live DVD or flash drive installer:

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by kvanoff on 2015-11-21
Thanks old Fred, you are absolutely right. Ill make two different threads to carry more water to my "store".

just, in which section shall i post the login problem?

---

### Post by oldfred on 2015-11-21
Not sure what is best location. If new user probably better in New to Ubuntu.
We try to be a little more detailed in responses there.
Also try to post more details on system and/or specific issue.
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

But I most often use New Posts to find new threads and often do not pay close enough attention to which part of forum thread is in.

---

### Post by grahammechanical on 2015-11-21
In case it has not occurred to you, it is possible to access that Ubuntu partition from a Ubuntu Live session and then backup your files. You can use GParted in a live session to create another partition and format it as Ext4 then copy any files you need to keep over to the new partition. Then if you need to re-install Ubuntu you can do so using the Something Else option without touching the partition with your data in.

Regards

---

