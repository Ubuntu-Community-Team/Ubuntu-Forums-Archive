---
title: "How do I change the 'root' user to 'jarjar' on this account I created?"
date: 2020-07-16
forum: General Help
---

### Post by chiques on 2020-07-16
deez@mancave-server:~$ sudo ls -la /home/balario/ftp/
total 8
dr-xr-xr-x 2 nobody nogroup 4096 Jul 16 12:26 .
drwxr-xr-x 3 root   root    4096 Jul 16 12:26 ..

---

### Post by Holger_Gehrke on 2020-07-16
The two entries for root are the owning user and group of the directory (folder) '..', which in this case means the directory '/home/balario/'. It's unusual for a directory in /home to be owned by root. This makes me think that you tried to create a new user by simply creating a directory in /home with 'sudo mkdir /home/balario/'. 

Is this what you've done ? Because that's not how it works ... To add a new user you would normally use adduser (see 'man adduser' for details) from the command line or if you are on a system with a GUI there should be some kind of graphical tool to do it (slightly different on each flavour of Ubuntu).

Otherwise the command to change the ownership of a file or directory is 'chown'. So if the user 'jarjar' exists you could just do 'sudo chown jarjar:jarjar /home/balario/' (the second 'jarjar' is the group of the same name as the user that Debian derivates create for every user).

Holger

---

