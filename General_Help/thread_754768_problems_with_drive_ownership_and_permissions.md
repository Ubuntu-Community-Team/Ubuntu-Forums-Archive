---
title: "problems with drive ownership and permissions"
date: 2008-04-14
forum: General Help
---

### Post by hazlik on 2008-04-14
help, i'm really new to ubuntu and linux,  and i'm having problems changing the ownerships for my drives.  for example the one labeled file system  is it even possible to change the ownership of that.   also i partitioned my slave drive for ubuntu but i can't seem to do anything with it except mount it and look at all the empty space...and suggestions would be greatly appreciated

thanx

---

### Post by njparton on 2008-04-14
You partitions are mounted into folders usually under /media or /mnt. These folders are like any other and each has an owner and a set of permissions.
 
e.g. to change the owner of a folder to bob:
 
```
sudo chown bob /media/folder
```
 
(obviously change 'bob' and 'folder' to suit your requirements).
 
To change the permissions for you folder you need to use chmod and you have the option to change read (r), write (w) and execute (x) permissions for the owner (u), the group (g) and other (o). Navigate to your /media folder and run the following command:
 
```
ls -l
```
 
this will show you a list of permissions for the folders in that directory.
 
To give yourself full access to a folder (assuming you're the owner):
 
```
chmod u+rwx folder
```
 
to remove access from anyone else:
 
```
sudo chmod go-rwx folder
```
 
etc etc
 
You don't need to use sudo for the chmod command if you're the owner of the folder

---

### Post by rogirwin on 2008-04-14
"df -h" will show what is mounted where.

Have a look at /etc/fstab to see what your system is going to mount when it boots.

---

### Post by vanadium on 2008-04-14
DO NOT change the ownerschip of your drive labeled Filesystem unless you are prepared to end up with a broken system,! By default, this belongs to root, the administrator of the system (that is you, after you typed the sudo command and your password).

For an empty slave drive obviously it is fine to give permissions to yourself as a user to write on it. Only the root (the administrator) is allowed to give somewone permissions, though (that is the build-in security of a unix/linux system).

You can use the "sudo chown" command shown by njparton. You might at first be more confortable with a graphical approach using the file manager. For this, you need to launch an instance of the file manager (nautilus) with root permissions. Either open a command prompt or press Alt+F2, and type

gksudo nautilus

Now you will be able to change permissions of directories within /media (right-click the directory, Properties tab). With this instance of nautilus, you can also screw up your system! Therefore, just do what you have to do and quit that instance of nautilus as soon as you are done!

---

### Post by hazlik on 2008-04-14
thanx everybody looks like its working ... hahaha

---

