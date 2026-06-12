---
title: "Weird permission for the newly created user"
date: 2015-03-01
forum: General Help
---

### Post by gopukrishnan on 2015-03-01
I have came across a situation where I am not sure why a user is getting weird permissions of a user that already removed from the system. I have created a user named harry and gave permission to a folder. I have removed the old user and added another user. Surprisingly the new user that is having the uid of the removed user is getting the permission of the old user had.






```
root@ubuntu2:~# mkdir /root/test
root@ubuntu2:~# ls -ld /root/test/
drwxr-xr-x 2 root root 4096 Mar  1 15:27 /root/test/
root@ubuntu2:~# useradd harry
root@ubuntu2:~# cat /etc/passwd|grep harry
harry:x:1001:1001::/home/harry:
root@ubuntu2:~# chown -R harry:harry /root/test/
root@ubuntu2:~# ls -ld /root/test/
drwxr-xr-x 2 harry harry 4096 Mar  1 15:27 /root/test/
root@ubuntu2:~# userdel harry
root@ubuntu2:~# ls -ld /root/test/
drwxr-xr-x 2 1001 1001 4096 Mar  1 15:27 /root/test/
root@ubuntu2:~# useradd tom
root@ubuntu2:~# cat /etc/passwd|grep tom
tom:x:1001:1001::/home/tom:
root@ubuntu2:~# ls -ld /root/test/
drwxr-xr-x 2 tom tom 4096 Mar  1 15:27 /root/test/

```



Here tom got access to the folder test harry had since he is having the same uid of the old user.


Thanks,
Gopu

---

### Post by TheFu on 2015-03-01
This is not a bug. It is working as designed.

That is Unix - it has been that way for 40-ish years. Disable old accounts and if you want to remove them, take ownership of all their files for a different userid. Reusing the uid (i.e. number), is about flexibility.

Oh - and there doesn't appear to be anything "weird" about those permissions.

---

### Post by gopukrishnan on 2015-03-01
Hi TheFu,

Thanks for your reply. I am not an expert and still learning. Having stated that, I think it is better to have a dedicated uid/user for these type of permissions rather than using the uid of the user removed from the system. By this way we can ensure that no new user get permissions to the folders unless we change it manually.

Gopu

---

### Post by bab1 on 2015-03-02
> **gopukrishnan said:**
> Hi TheFu,

Thanks for your reply. I am not an expert and still learning. Having stated that, I think it is better to have a dedicated uid/user for these type of permissions rather than using the uid of the user removed from the system. By this way we can ensure that no new user get permissions to the folders unless we change it manually.

Gopu
The files and folders are always owned by the uid/gid.  The user name is for human convenience.  As @TheFu said you don't delete the user (uid/gid) until you move that user files to a different place and change the ownership to an appropriate name (uid) or delete all the files.  This can include backups of the data too.

Since you have 65536 unique uid/gid numbers I cant see how disabling a user ID on a permanent basis is such a big deal.  I'd say learn the system before looking to modify it.

---

### Post by gopukrishnan on 2015-03-08
Thanks all for your replies..I will disable rather than deleting the user.

---

