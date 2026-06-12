---
title: "How to assign permitions to only home directory and omit all other reads to other dir"
date: 2008-02-06
forum: General Help
---

### Post by abcuser on 2008-02-06
Hi,
In Ubuntu 7.10  I created new user 'user1' from System | Administration  | Users and Groups. This user has /home/user1 home directory. I would like to omit that user1 can only read/write/execute in his/her home directory, all other directories he/she must not have access to. I don't like that 'user1' has read access to directory /etc/passwd, /etc/group... 

Is there any simple way to omit user1 all file permissions to all directories and files on file system except to directory /home/user1?
Thanks,
Abcuser

---

### Post by zarqoon on 2008-02-06
I do not think its possible to particulary exclude a user. But you can exclude all except some that are particulary autorized. 
Most files have read access enabled for other you just have to disable that so that only group members and the owner of that file may read it. 
But you most definatly dont want to take all rwx permits except its home away from any user because that would effectively make that user unuseable. If you take away permits for the /bin folder that user wont even be able to do an ls or start anything for that matter. He should not even be able to log in. If you take away permits for the whole /etc folder all kinds of programs that are not run with superuser privilegies would not be able to read their config files. You could of course take read permits away for certain files but you should be sure you really dont need them. If you do a "chmod o-rwx" on a  file belonging to root that is needed to read for login and your root login is disabled you may not be able to login with any user at all.

---

### Post by abcuser on 2008-02-07
zarqoon,
thank you very much. That was really good answer.
Thanks,
Abcuser

---

