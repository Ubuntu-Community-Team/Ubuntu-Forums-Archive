---
title: "need help to set permissions with GID"
date: 2007-02-21
forum: General Help
---

### Post by mojoman on 2007-02-21
Hi,

I need some help with a permission problem, running 64-bit dapper. The /home is on a separate partition. I got a two users on my desktop, each with a separate directory (/home/user1 and /home/user2). permissions in those two home-folders are just fine.

I also have a couple of other folders in the /home, folders where I keep stuff both users need access to (e.g. /home/stuff1, /home/stuff2 etc). Now, I need all files created or saved in those directories to have permission set as 770 (or maybe 774). i.e. readable, writable and executable by owner and group but not accessible for the world.

I created a group (called private) and made user1 and user2 members of that group. I set the group ownership for the folders as private. I then set the GID on these folders (sudo chmod g+s stuff1 stuff2 etc). So far, so good. Everything created in those folders now belongs to group private. However, the permissions for group members are no good. 

Here are (some) of the folders in /home and the permissions i gave them:
```

drwxrws---  9 root     private   4096 2007-02-21 20:47 download
drwx------  2 root     root     16384 2006-09-18 20:32 lost+found
drwxr-x--- 64 mojoman  mojoman  16384 2007-02-21 20:54 mojoman
drwxr-xr-x  2 root     root      4096 2007-02-21 14:58 Recycled
drwxrws---  2 root     private   4096 2006-12-10 08:08 temporary
drwxrws---  7 root     private   4096 2007-02-20 20:09 upload
```

Now, my user mojoman belongs to group private so that's not the problem. Also, when a create a new file in, for example, the download directory, it got these permissions:

```
-rw-r--r-- 1 mojoman private       0 2007-02-21 21:18 newfile
```

Right group, wrong permissions. I've understood (i think) that umask determines the permissions on newly created files but I don't want to change it in all circumstances, I just want it to apply in these specific folders.

So, question is, how can I set it up so that all files and directories created in these subdirectories of home (i.e. /home/stuff1, /home/stuff2 etc) automagically gets permission 770 or 774?

Any ideas, anyone?
/mojoman

---

### Post by markitect on 2007-03-01
umask will set the default permission, from you command prompt type umask to print the current setting
and umask XXXX to set a new one.  It works opposite of chmod so 0 is everything 7 is nothing.  so ```
umask 0007
``` give all permissions to user and group none to everyone ```
umask 0003
``` allows everyone read access, etc.

---

### Post by mojoman on 2007-03-02
> **markitect said:**
> umask will set the default permission, from you command prompt type umask to print the current setting
and umask XXXX to set a new one.  It works opposite of chmod so 0 is everything 7 is nothing.  so ```
umask 0007
``` give all permissions to user and group none to everyone ```
umask 0003
``` allows everyone read access, etc.

Yep, it does BUT the question is how I can set this for just a couple of specific directories? This setting would be in /etc/profile and I reckon I need some sort of script there in order to accomplish this but I have no idea how to go about this. 

Any ideas, anyone?

/Mojoman

---

### Post by mojoman on 2007-04-19
I hope I'm not too obnoxious if I bump this thread but if anyone could give me some help on this one it would seriously make more than my day. I mean, at least my week. 

/mojoman

---

