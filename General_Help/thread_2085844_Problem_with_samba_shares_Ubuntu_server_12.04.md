---
title: "Problem with samba shares Ubuntu server 12.04"
date: 2012-11-19
forum: General Help
---

### Post by craig smith on 2012-11-19
I'm having a problem with setting up samba share permissions on ubuntu server lts. I've got two shares set up in the smb.conf file. Their entries look like this:

[share]
comment = Ubuntu File Server Share
path = "insert real path name here"
browsable = yes
guest ok = no
read only = no
create mask = 0700
group = group1

[media]
comment = Ubuntu File Server Share
path = "insert real path name here"
hide unreadable = yes
browsable = yes
guest ok = no
read only = no
group = group2
create mask = 0700

now, in the file system I am the owner of all directories related to both these shares. the [media] share group owned by group2 and the [share] is group owned by group1. Also for both directories I have file permissions set at 771, where owner has read, write, and exicute. Group had read, write, and exicute. Guests have only exicute. (i think this i right)I have 3 users in the system, myself, my wife, and my mother. I belong to group1 and group2, as does my wife. My mother belongs only to group2. When I log into the server from my windows desktop my credentials work as expected. But if I use my wife's or my mother's nothing works. They can log into the server but when you click on one of the shared folders another log in screen is displayed asking for another username / password. This always fails and they are not allowed access to the folders. I would like for my wife and I to have access to both of these folders while restricting access to other users. What am I missing here? I've tried fixing this for quite some time and I can't seem to get it figured out. Thanks for any help!!

---

### Post by craig smith on 2012-11-19
found the problem. firstly I didn't know that there was a samba password that needs to be assigned for each user. second the line group = group1 needed to be changed to write list = @group1. group was found by the config file checker to be invalid. Can anyone tell me why after assigning the samba passwords, users were able to bypass the file system permissions to be able to see the contents of both folders? I've since fixed it, but it seems that if a unix user doesn't have permission to view a file then a samba user would also not be able to view a file.

---

