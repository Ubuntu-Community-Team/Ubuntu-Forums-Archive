---
title: "Mounting partition into /home/user"
date: 2013-03-15
forum: General Help
---

### Post by longbeard on 2013-03-15
I am always struggling with Ubuntu 12.04 security measures! I'd like to get hold of the following:

a) How can I set the "executable" bit on a program or script? So far no attempt successful, no way.

b) I intend to mount an empty ext4 partition with mount point "/home/user/something". Logged as "user" I edited fstab with 
gksu gedit /etc/fstab and set options with "user,auto,exec" etc.
The partition shows in directory but is unfortunately the branch is locked. When I open the partition on the side-bar it says its owner is "root" and I cannot modify it. Splendid!
How can I make this partition available to the user? 

Thanks for advice on a difficult system!

---

### Post by Morbius1 on 2013-03-15
>  a) How can I set the "executable" bit on a program or script? So far no attempt successful, no way.
You should be able to do this graphically but you can do it in a terminal:
```
sudo chmod +x /path/to/script
```
This of course assumes the script resides on a Linux filesystem and not a Windows filesystem.
> I intend to mount an empty ext4 partition with mount point "/home/user/something"
A newly created ext4 partition will mount with owner = root and permissions of 755. If you are the only user then take possession of the mounted partition:
```
sudo chown user /home/user/something
```
Change "user" to your own login user name.

---

### Post by schragge on 2013-03-15
> **longbeard said:**
> set options with "user,auto,exec" Options *user* and *auto* make little sense when used together. Usually, either the partition gets *auto*matically mounted by root when booting the system or it gets manually mounted by *user*. Besides, *auto* is set by default, no need to specify it explicitly.

---

### Post by rnerwein on 2013-03-15
hallo
how does the whole line of your mount command is. what kind of system you want to mount. how is the server (export) configured for the fs to mount. on your side the
default for mount is:  Use default options: rw, suid,  dev,  exec,  auto,  nouser,  and async.
but the master is the server !!!! ;-)
ciao

---

