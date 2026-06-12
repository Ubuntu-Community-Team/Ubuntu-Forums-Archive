---
title: "Permanent directory permissions"
date: 2013-06-13
forum: General Help
---

### Post by DudeBud on 2013-06-13
Hey guys,

[FYI: Searched forums before asking question]

So this, in my mind anyways, should be a simply question....  How do i permanently set directory permissions (also recursively) on a folder to 777 that WILL NEVER change until i want them to.
 
Simple enough... right?

I tried "sudo chmod 777 -R" to solve my problem, but its persistent.

I have a Ubuntu server setup, with a samba share, and media server that is constantly in use by the family.  Everything gets dumped into /media/TheGrid on the server and accessed by windows machines and our BOXEE.  Now i run rtorrent to download "stuff" for later viewing, and whenever i use the server and move files around on /media/TheGrid (SSH as root or another user) all the files i touch revert back to their "user" ownership permissions.  Even when i create new directories in the samba share i lose previous permissions.  
 
Everytime i add a new file i need to run: chmod 777 -R /media/TheGrid otherwise i can't use it.
Samba is set to inherit permissions.

My buddy told me that a "sticky bit" might help me here.... but i'm not sure how to implement this.
Do i need to create a script to keep chmod-ing???? I need a solution that will survive reboot.

I want to create a directory that will always be 777, and when a file is added to this directory its permissions will change to 777. ALWAYS!!!

I'm just tired of running "chmod 777" every 5 minutes.
There has got to be a better way.

 Thx for the help.

---

### Post by newbie-user on 2013-06-13
There are samba configuration settings that automatically set the permissions for all new files and folders that are created. In /etc/samba/smb.conf, uncomment and change the following lines to suit your permission needs:
```
;   create mask = 0700
;   directory mask = 0700
```

By default, samba allows rwx for the owner of the file folder. Change the permission sets to 777, then restart samba. All files/folders created thereafter should have 777 permissions.

---

### Post by albandy on 2013-06-13
First create a group:

sudo addgroup sambatorrrentusers

then add users to the new group

sudo adduser myuser sambatorrrentusers
sudo adduser user2 sambatorrrentusers
sudo adduser user3 sambatorrrentusers
sudo adduser user_of_torrent_server sambatorrrentusers

Finally set the permisions to the samba shared folder

setfacl -d -m sambatorrrentusers:rwx /your/samba/shared/dir

After that restart the computer (It's not necessary but faster than restarting services and sessions)

---

