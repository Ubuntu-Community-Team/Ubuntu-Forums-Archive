---
title: "Change folder permissions"
date: 2013-03-14
forum: General Help
---

### Post by caleb12134 on 2013-03-14
I want to change permissions of a file so any user can add files to the folder /var/www on my apache web server so i can add web files.

---

### Post by Bashing-om on 2013-03-14
caleb12134; Hi !

All one wants to know about permissions and how to use them:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[INDENT=2]
HTH

[/INDENT]

---

### Post by caleb12134 on 2013-03-15
can someone give me an example with all permissions??

---

### Post by mckenna1977 on 2013-03-15
chmod 777 <filename>

chmod -R 777 <directory>

---

### Post by caleb12134 on 2013-03-15
Ok so i will explain in more details??
So i want to change the permissions of a file in my apache web server so that i can edit and add files from my current  ubuntu desktop account??? The file path is /var/www/multicraft    ??? How would I give this file all permissions to everyone?? it says im not the owner???Please help me :)

---

### Post by Bashing-om on 2013-03-15
caleb12134; 
specifically...not a problem at all. Just be aware of the warnings in arbitrarily  assigning access.
> I would like to point out that the following command is not necessarily a good idea:
Quote:
sudo chmod -R 777 /<some directory>
It will make every subdirectory executable which is what you need in order to open it to see what's inside and to work with it. But it will also make every file executable as well, maybe not at all your real intent ! 

An alternate way that works around this problem is to use something like this:
```
Code:sudo chmod -R a+rwX /var/www/multicraft
```

All subdirectories will be marked rwx for user, group, and others. The big "X" will also not make files executable unless they were executable to begin with. There is no way to reproduce this using octal notation.[INDENT=4]
just pass'n it on

[/INDENT]

---

### Post by cigtoxdoc on 2013-04-04
This is a very useful tip.  The gods of Ubuntu keep wanting to protect us from ourselves and set up traps to keep us from moving files in our own home directory and subdirectories.  Using sudo chmod -R a+rwX on /home/myname and its subdirectories has saved much frustration and time.

John

---

### Post by 3rdalbum on 2013-04-04
1. Please don't bump threads that are two weeks old with off-topic messages.

2. Ubuntu does not limit your access to your home directory. If you've been using root access incorrectly you may have inadvertantly restricted permissions in your subfolders.

3. It's a bad idea to loosen the permissions of /var/www - instead, use sudo to copy files to that folder.

---

