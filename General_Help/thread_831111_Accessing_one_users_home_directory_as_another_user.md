---
title: "Accessing one users home directory as another user"
date: 2008-06-16
forum: General Help
---

### Post by cafeman on 2008-06-16
Hi all hope you can help.

I've set up a home server so me and my wife can both work on the same website.  The files are in her home directory like so:-

/home/herusername/website/

However I can navigate the files but I can't change them when logged in as me!

How can I gain full access to those files on her home with my login?  We both need separate logins but also to have full access to these files.  Is there something I can do with groups?  Perhaps by adding my username to her group?  I tried it and it didn't work but ... ?

---

### Post by Keith Hedger on 2008-06-16
This is a permissions problem u can would be better off moving the folder out of your wifes home folder and setting the permissions of the folder ie right click->properties->permissions or u can use the chmod command from the cli

---

### Post by cafeman on 2008-06-16
But how do I set the permissions of the folder to be accessable by each of us equally?  We are both mapping in from XP machines, so as you can appreciate we both have our own logins on them and therefore need to maintain different username/passwords.  I would like to know how to set up the linux server to allow us to both access fully this directory.

---

### Post by bingoUV on 2008-06-16
1. It quite beats one of the purposes of having separate accounts if you can change each other's files. If you make a mistake, her files might be gone. If you acquire a virus (not yet for linux, but we should be prepared) her files are in danger. If you run a script from some untrusted source, it could screw up her files. Permissions are so that you alone are harmed by your mistakes/misfortunes/misadventures.

2. If you insist, do the following. 

a. Create a group called couple (from System -> Administration -> Users and Groups).
b.  Now, for the files/directories that need access from both of you, change their group owner to couple. Right click on file/directory, properties, permissions, group.  
c. Now change the permissions of the files to allow group write. Right click on file/directory, properties, permissions, group, file access or folder access).
d. Now add both your users into the group couple (from  System -> Administration -> Users and Groups).

Do this only where absolutely necessary.

PS : Logout and login again for your new group permissions to take effect.

---

### Post by tgrimley on 2008-06-16
could you post the output of ```
ls -al /home/herusername/website
```

---

### Post by cafeman on 2008-06-16
Thank you very much for your help.  Would I have to do this on each new file created though?  For example, I create a file and then my wife wants to alter it, would I have to go in and change permissions etc. before she was able to do this?

---

### Post by mssever on 2008-06-16
I don't know how Samba might complicate this, but from the Linux side, I'd recommend creating a new group for this purpose. Then add yourself and your wife to that group. Run [sudo]sudo chgrp -R your_new_group /website/folder[/code] to change the group of the website folder and its contents to your new group. Finally, give write permission to the group: ```
sudo chmod g+w /website/folder
```I don't know whether Samba is smart enough to figure this out and properly maintain the permissions.

EDIT: Others posted while I was typing.

---

### Post by cafeman on 2008-06-16
> **tgrimley said:**
> could you post the output of ```
ls -al /home/herusername/website
```

drwxr-xr-x  4 helen helen 4096 2008-06-06 18:04 .
drwxr-xr-x 31 helen helen 4096 2008-06-06 17:42 ..
drwxr-xr-x  9 helen helen 4096 2008-06-16 10:55 homephotosweb
drwxr-xr-x  2 helen helen 4096 2008-06-06 18:05 testweb

---

### Post by bingoUV on 2008-06-16
A better solution is to create a user 'website' and login through this to create the website. To switch quickly between users, Right click on panel, Add to panel, 'User switcher'. Her home should be her own property.

---

### Post by mssever on 2008-06-16
> **cafeman said:**
> Thank you very much for your help.  Would I have to do this on each new file created though?  For example, I create a file and then my wife wants to alter it, would I have to go in and change permissions etc. before she was able to do this?
I believe that new files inherit the group of the directory they're in. But they don't inherit permissions. Ubuntu's default umask is 0022. If you change it to 0002, then new files will be group-writable by default.

---

### Post by tgrimley on 2008-06-16
> **cafeman said:**
> drwxr-xr-x  4 helen helen 4096 2008-06-06 18:04 .
drwxr-xr-x 31 helen helen 4096 2008-06-06 17:42 ..
drwxr-xr-x  9 helen helen 4096 2008-06-16 10:55 homephotosweb
drwxr-xr-x  2 helen helen 4096 2008-06-06 18:05 testweb

These aren't group writable so even if you're in her group it won't let you write to them :) you'll need to chmod g+w the directory and then make sure the umask is group writable.. like the poster above suggests

---

### Post by cafeman on 2008-06-16
OK, so I did the following:-

sudo useradd cafeman
sudo passwd cafeman
sudo groupadd usboth
sudo usermod -a -G usboth cafeman
sudo usermod -a -G usboth helen
sudo chgrp -R usboth /home/helen/webpages
sudo chmod g+r /home/helen/webpages

helen@testserver:~# ls -la /home/helen/webpages/
total 16
drwxr-xr-x  4 helen usboth 4096 2008-06-06 18:04 .
drwxr-xr-x 31 helen helen 4096 2008-06-06 17:42 ..
drwxr-xr-x  9 helen usboth 4096 2008-06-16 10:55 homephotosweb
drwxr-xr-x  2 helen usboth 4096 2008-06-06 18:05 testweb

And I can navigate to the /webpages/ directory from my machine and open the files but I can't write to them :(

---

### Post by tgrimley on 2008-06-16
did you mean to do this ```
sudo chmod g+r /home/helen/webpages
```

I think you mean to do g+w

---

### Post by cafeman on 2008-06-16
Crap I did you're right, thanks!

So now I can browser and edit everything there, but when I just created a new file I then went over to my wifes computer and she can see it but has no write permission on it herself!  Is there a setting in SAMBA perhaps that would make sure it was created with the correct permissions so we can both read and write each others creations?

---

### Post by cafeman on 2008-06-16
In fact I just looked at the file with ls -la and:-


drwxrwxr-x 2 helen usboth 4096 2008-06-16 22:09 .
drwxrwxr-x 4 helen usboth 4096 2008-06-06 18:04 ..
-rwxrw-r-- 1 helen usboth 10 2008-06-16 22:10 index.html
-rwxr--r-- 1 cafeman cafeman 3 2008-06-16 22:09 test.txt

So I guess that proves that it created it as mine rather than group 'usboth'.  I wonder how I get SAMBA to create files as 'cafeman usboth' for me and 'helen usboth' for my wife?

---

### Post by unutbu on 2008-06-16
**To change your default group permissions:**

```
-rwx**r--**r-- 1 cafeman cafeman 3 2008-06-16 22:09 test.txt
```
Currently, your default group permissions is set to read-only. To change your default group permission to read, write and executable (when appropriate), you need to edit your ~/.profile to include

```
umask 0002
```
User helen would have to do this too.

**To change your default group ID:**

Your /etc/passwd probably looks something like this:
```

cafeman:x:1000:**1000**:Cafeman,,,:/home/cafeman:/bin/bash
helen:x:1001:**1001**:Helen,,,:/home/helen:/bin/bash
```

According to `man passwd`:
The colon separated fields mean
> 
       ·  login name
       ·  optional encrypted password
       ·  numerical user ID
       ·  **numerical group ID**
       ·  user name or comment field
       ·  user home directory
       ·  optional user command interpreter
Your 4th colon separated field equals 1000. That means cafeman. That's why files you create have default group ID 'cafeman'. Similarly, helen's field equals 1001, which means 'helen'.

Unfortunately, you only get to define your default group ID once for your user -- you can't set it to usboth specifically for the /home/helen/webpages directory.

Here are some options:
1) Run a script which can monitor the webpages directory and whenever it detects a file whose group ID is not usboth, will change the group ID to usboth. You can set the script to run at boot time, so you wouldn't have to do anything once the script is setup. The problem is I don't have such a script handy at the moment, but I wouldn't mind working on this, and could probably whip something up in a day or two.
2) Use 
```

sudo usermod -g usboth cafeman
sudo usermod -g usboth helen
```
This will change both yours and helen's default group ID to usboth. However, this change would be global -- all files you create from then on would have group ID usboth. I don't know if that's what you want. Coupled with umask 0002, it would lead to all your files being readable and writable by both of users.
3) Maybe someone else knows a better third option?

---

### Post by cafeman on 2008-06-16
OK got it to all work properly with this in smb.conf

[cafeman]
path = /home/helen/webpages
valid users = @usboth
available = yes
browsable = yes
public = no
writable = yes
force group = usboth
inherit acls = yes
create mask = 0660
directory mask = 0770

[helen]
path = /home/helen/webpages
valid users = @usboth
available = yes
browsable = yes
public = no
writable = yes
force group = usboth
inherit acls = yes
create mask = 0660
directory mask = 0770

Now when I create something via my windows machine she can edit it and vice versa... perfect.

Thanks all for your help!

---

### Post by unutbu on 2008-06-16
I'm glad you found a better third option!

---

