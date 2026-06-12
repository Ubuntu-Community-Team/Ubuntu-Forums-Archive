---
title: "/host folder taking up all my space"
date: 2013-10-17
forum: General Help
---

### Post by jforkum on 2013-10-17
I recently tried installing a game onto my home directory, but it told me I didnt have enough free space. Knowing that I allocated a 215 gb partition for Ubuntu when I installed it, I went to check my total hard drive space. I found that I had almost 198 gb of free space. Confused, I went to the /(root) directory and right clicked on the home folder, clicked properties, and on the very bottom of the basic tab it tells you your free space. I only have 5 gigs of free space in my home folder. (5.7 used) I started checking all the other directories (bin,boot,dev,etc,home,host,lib,lib32,lib64,lost+found,media,mnt,opt,proc,root,run,sbin,selinux,srv,sys,tmp,usr,var).
A few of them, like proc, were un readable, which is to be expected. But all of the ones I could read only had 5 gigs of free space... except for host. Host had 193.7 gigs of free space and 21 used!!! Thats where all my free space went! 

Can someone tell me how to take some space from host and add it to my home folder?

---

### Post by oldfred on 2013-10-18
If you have a /host, then that is a wubi install inside a NTFS partition. Wubi has a limit of 30GB. Normally if allocating a partition you want a full install. One of the advantages of wubi was that no partitioning was required.
Wubi also is being phased out as it is not compatible with gpt partitioning which all new UEFI system have.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)


 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

      
 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

