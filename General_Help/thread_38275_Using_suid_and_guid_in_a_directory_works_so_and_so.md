---
title: "Using suid and guid in a directory works so and so"
date: 2005-05-30
forum: General Help
---

### Post by jobezone on 2005-05-30
Hello everybody,

I'm having a bit of a problem with the suid and gui feature in a directory.

This site [http://kurt.www.pinboard.com/techwritings/d83/](http://kurt.www.pinboard.com/techwritings/d83/) tells me:
> 
When [the suid bit is] set on a directory, all the files and directories created within this directory will have the same owner as the SUID-directory itself, no matter who created the file.

This would be helpfull for me, since I want to have a directory wich is equally shared by all users, and to be used by amule. This way, only one instance of amule is run (in my case I'm running amuled as a deamon), and all users can use amulegui to start/stop transfers. All the downloaded files would be placed in the user amule's home directory, for anyone to take. I also intend to make this the multimedia folder all users use to listen to musics, watch movies, etc, and also share them, thus my need for all files placed there be "reowned" by amule. It worked a few times, it seemed, but not anymore.

These are the permissions of /home/amule/ 
```
drwsrws---  7 amule amule 4096 2005-05-30 23:58 amule/

```

It's got the "s" in the correct places, right?
Now, me, as a user, and being in amule's group, as shown in /etc/group
```

amule:x:1002:eduardo

```
go to the directory /home/amule, and create a file.
```

eduardo@supercow:/home/amule$ echo whatever > ola.txt
eduardo@supercow:/home/amule$ ls -al ola.txt
-rw-r--r--  1 eduardo amule 7 2005-05-31 00:13 ola.txt
eduardo@supercow:/home/amule$

```
As you can see, the new file belongs to group amule, but is owned by me.
It is also made unwrittable by Group, which is something I don't want.

Any unix/linux guru could help me out? Or is what I want something impossible?

---

### Post by thrift on 2005-05-30
Your GUID bit appears to be working correctly and this should be enough to accomplish what you are looking for.  I have never tried using the SUID bit on a directory, so I don't know what's going on there, but I am having no luck here either.

You need to change your umask so that when you write to that directory your files will have the correct group permissions.

Try out 

umask 0007

and see if that fits your liking a little better.

You may want to look into using ACLs if you need something more than that.  They can do what you are looking for, but umask and GUID bit should be sufficient.

---

### Post by jobezone on 2005-05-30
Perhaps  I will look into ACL, because I also want users not to be able to write into each others home dirs.
Thanks for the tip on unmask!

---

### Post by thrift on 2005-05-31
No problem, but for reference you don't need ACLs to keep users from writing to each others home directorys.  

By default users shouldn't be able to write to each others home directorys.  and if you own the home directory to the user private group or change the group permissions to be more restrictive you can restrict the settings a lot more without needing to use ACLs.

---

### Post by jobezone on 2005-05-31
Ah, you're right, the home dirs belong to the user private group, so umask will be what I need. Thank you for helping me out.

---

### Post by jobezone on 2005-05-31
For posterity searchers, welcome!

Well, defining umask for a user seems to be more trouble than it should.  /etc/login.defs defines a default umask,but only works in shell logins, not with gdm or kdm. After searching a bit with google on the debian lists, I read about package libpam-umask . It must be recent, it's at 0.0.1 version :) Description:
> 
This PAM module sets the umask for successfully authenticated sessions.
 The umask affects the permissions assigned to newly created files by
 default.
 .
 This package is useful to ensure that users' umasks are set consistently
 whether their session is initiated by login, SSH, a display manager for
 the X Window System, or some other means.


I then edited /etc/pam.d/gdm and added the line:
```

session    optional     pam_umask.so umask=0007

```
as explained in its documentation.
Because I still have to logout and login to see if this works, it's still untested. I will check it now, and edit this with the results.

---

### Post by thrift on 2005-05-31
A PAM module.  Very cool.  Let us know if this works.

---

### Post by jobezone on 2005-05-31
It didn't work, but it did make changes. Files I created in gnome where create with permissions to read and write by the owner, and none to the group and others, which is not what I wanted, as I wanted for group to also be able to read and write.

For now, anyone copying files to the shared folder will himself change the propreties to allow for group to write, as this is quite easy graphically. In the future maybe I'll try this again, with different umask values in /etc/pam.d/gdm ...

---

