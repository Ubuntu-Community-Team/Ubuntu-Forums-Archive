---
title: "Cannot access folders created by Samba as Ubuntu user"
date: 2014-11-01
forum: General Help
---

### Post by STFU Donny on 2014-11-01
Hello Ubuntu community. I have created a samba share on my xubuntu computer. I can login to it just fine from windows and create folders, etc. However, I cannot read or write to these folders when I am logged in on my xubuntu computer. Please see below for an update. [s]I'm sure this is an easy fix but I don't understand about the numeric permissions so here is my smb.conf. I think I just need to change one of these numeric values. [/s]

[s]```
Under #Authentication#, security = user 

[Samba]
comment = Samba Share
path = /media/USBHDD1/shares
valid users = @users
force group = users
create mask = 0660
directory mask = 0771
read only = no
```[/s]

Let me know if you need more from the smb.conf. [s]If it is just changing the create and directory mask, please explain what these are in a simple manner :)[/s]

Thank you.

---

### Post by STFU Donny on 2014-11-02
Did I post this in the proper subforum?

---

### Post by STFU Donny on 2014-11-15
I've since been able to make a directory created under windows readable by my xubuntu user named jrd. But I cannot get it to be writable without manually doing a chmod. The directory is just music and stuff so I don't care if it's 777.

my current smb.conf:
```
[Samba]
comment = Samba Share
path = /media/USBHDD1/shares
browseable = yes
read only = no
writable = yes
valid users = jrd @users
create mask = 0777
directory mask = 0777
```

testparm output (I don't understand this):
```
[Samba]
	comment = Samba Share
	path = /media/USBHDD1/shares
	valid users = @users
	read only = No
	directory mask = 0777
	locking = No
	strict locking = No
	available = No
```

ls -l output of the directory created in windows (note r-x instead of desired rwx at the end)
```
ls -l
total 56
drwxrwxr-x  2 samba users  4096 Nov 15 16:17 New folder (4)

```

---

