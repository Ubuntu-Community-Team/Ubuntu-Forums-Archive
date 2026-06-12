---
title: "setting up proper permissions for various purposes on a drive"
date: 2016-01-02
forum: General Help
---

### Post by NotQuiteSU on 2016-01-02
I'm running Ubuntu Server 14 LTS... It's a clean build and I just added a 3 TB drive to it to be storage for all things, including home directories when I move them over. I want to also have folders for all the media that most users have full access to, and maybe some only have RO access.

**Users:**
root
User1
User2
User3 (RO)

**Groups**
htpc - all users are a part of this group except User3

which user:group should own /media/disk1, so that users can have their own private home folders underneath disk1, as well as other folders which all have access.

**/media/disk1**
User1-home (user1 700)
User2-home (user2 700)
music (775)
movies (775)

If I make /media/disk1 to be root:htpc, wouldn't everyone in group htpc have access to User1-home, regardless of permissions since I set them on /media/disk1?

---

### Post by papibe on 2016-01-02
Hi NotQuiteSU.

Regarding your last question: you don't need to worry about /media/disk permissions. A standard 755 would do.

To understand this take a look at the /home directory and your own user home:
```
$ ls -ld /home
drwxr-xr-x 4 root root 4096 Oct 17  2014 /home

$ ls -ld /home/user/
drwxr-x--- 59 user user 4096 Jan  2 10:49 /home/user/
```
In other words, anybody can 'cd' and 'ls' in /home, but underneath /home each directory (like 'user' in my example) would determine the rules under it.

The permissions in /home itself only would be relevant if you want to allow access to create files or folders directly under it.

Does that help? Let us know how it goes, and if you need more help setting up cross permissions.
Regards.

---

### Post by NotQuiteSU on 2016-01-03
Thank you. So folder level supercedes permissions of parent folders. 

So who should own /media/disk1/? Almost Everyone should be able to write. So should I make another folder and grant permissions there? Or just leave them as root:htpc?

---

### Post by Dennis N on 2016-01-03
> **NotQuiteSU said:**
> Thank you. So folder level supercedes permissions of parent folders. 

So who should own /media/disk1/? Almost Everyone should be able to write. So should I make another folder and grant permissions there? Or just leave them as root:htpc?

I assume the new disk is an internal SATA drive? When you create a new partition on the new disk, the file system on that new partition is initially owned by root, and the group is root. The root folder of the new file system is the mount point you set in fstab (like /mnt/data).

If the file system is for data storage (not an operating system install) I immediately make my user (administrator) the owner and group of the root folder. If it is intended for installing an operating system, you leave it alone.

Then I make subfolders inside the root folder for different purposes.

---

### Post by NotQuiteSU on 2016-01-03
Perfect. That's exactly what I did. This is a secondary hard drive. I do have my permissions set up correctly. 

I consider this closed and solved. (I'll update my title shortly.)

---

