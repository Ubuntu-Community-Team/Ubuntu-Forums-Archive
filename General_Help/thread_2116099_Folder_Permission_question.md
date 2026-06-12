---
title: "Folder Permission question"
date: 2013-02-14
forum: General Help
---

### Post by BStrizzy on 2013-02-14
Hey guys,

I recently added a couple of people to my home server and the way I am setting it up is that they can access my external hdd that is mounted to my server. I have some school work in a folder that i would like them to have read only permissions. from my research and to my knowledge if I want to make this happend I simply have to do a 

```
sudo chmod 740 /home/cj/entertainment/school/ 
```

by doing this, this should not allow the user, cj, to delete any files, but for some reason when i log in as cj via ssh i can still delete files and stuff.

advice?

---

### Post by Bashing-om on 2013-02-14
BStrizzy; Hi !

Permissions: ->(r)ead (w)rite (x)ecute
rwx = 111 (binary) = 7 (decimal)
rw- = 110                  = 6
r-x = 101                  = 5
r-- = 100                   = 4
--- = 000                   = 0

owner  group  others
7             4          0

means that the owner "cj" has full permissions. //rightfully so as it is in his home directory//
```
ls -l <directory>[/]<file>
``` to see the permissions.

Might I suggest, for a solution, to set up a shared folder to share files with others ?[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by papibe on 2013-02-14
Hi BStrizzy.

740 wouldb't be my first choice. Here's why:

By default Ubuntu users are assigned to its own unique group, which is named after the user itself. Then, two random users won't belong to the same group. Thus the 4 in 740 won't let them access the files.

It would be easier to use the others bits: 754. But that would give read access to all users.

Another solution would be to create a group specially for sharing the files, then add yourself and your friends to the group. Finally change the group ownership of the directory:
```
sudo chown -R youruser:newgroup /home/cj/entertainment/school/
```
A final note, you need execute permission to the directory if you want your friends to 'cd' to it. Then I would do:
```
find /home/cj/entertainment/school/ -type **d** -exec chmod 750 '{}' \;

find /home/cj/entertainment/school/ -type **f** -exec chmod 740 '{}' \;

```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by rnerwein on 2013-02-15
> **BStrizzy said:**
> Hey guys,

I recently added a couple of people to my home server and the way I am setting it up is that they can access my external hdd that is mounted to my server. I have some school work in a folder that i would like them to have read only permissions. from my research and to my knowledge if I want to make this happend I simply have to do a 

```
sudo chmod 740 /home/cj/entertainment/school/ 
```by doing this, this should not allow the user, cj, to delete any files, but for some reason when i log in as cj via ssh i can still delete files and stuff.

advice?
hi
oh yes you can delete it. why --> in unix/linux you ain't delete the file (and its contence).
your folder school, i guess, looks like "drwxrwx000". but for sure it is set for write permission for the group. now back to "rm". if you delete a file in a folder (wich is a file too) you only delete the inode entry. there for the file is unvisible with ls but the contens is still on the disk. just give the file the sticky-bit.
using e.g.: chmod 1750 that gives you the permissions: drwxr-x--T . that means: owner can do anything, group can only read and walk around and other can do nothing.
on the system have a look at /tmp
cheers

---

### Post by bab1 on 2013-02-15
> **rnerwein said:**
> hi
oh yes you can delete it. why --> in unix/linux you ain't delete the file (and its contence).
your folder school, i guess, looks like "drwxrwx000". but for sure it is set for write permission for the group. now back to "rm". if you delete a file in a folder (wich is a file too) you only delete the inode entry. there for the file is unvisible with ls but the contens is still on the disk. just give the file the sticky-bit.
using e.g.: chmod 1750 that gives you the permissions: drwxr-x--T . that means: owner can do anything, group can only read and walk around and other can do nothing.
on the system have a look at /tmp
cheers
I think you will find that the *users* need to **NOT** be a member of the group with rw rights.    The directory /tmp is setup with world writable rights (i.e. 1777).  In this case only the owner has the right to delete the file a file he created ever though any user can create there own files.  If the another user was part of the group they would also be an owner.  See /tmp```

ls -ld

drwxrwxrwt 13 root root 4096 Feb 15 04:52 /tmp

```... and the files therein```

ls -l /tmp
drwxrwxrwt 2 lightdm lightdm 4096 Feb 15 03:49 at-spi2
drwxr-xr-x 2 root    root    4096 Feb 15 04:49 hsperfdata_root
...

``` 
See the relevant portion of```
man chmod
```

---

### Post by rnerwein on 2013-02-15
> **bab1 said:**
> I think you will find that the *users* need to **NOT** be a member of the group with rw rights.    The directory /tmp is setup with world writable rights (i.e. 1777).  In this case only the owner has the right to delete the file a file he created ever though any user can create there own files.  If the another user was part of the group they would also be an owner.  See /tmp```

ls -ld

drwxrwxrwt 13 root root 4096 Feb 15 04:52 /tmp

```... and the files therein```

ls -l /tmp
drwxrwxrwt 2 lightdm lightdm 4096 Feb 15 03:49 at-spi2
drwxr-xr-x 2 root    root    4096 Feb 15 04:49 hsperfdata_root
...

```See the relevant portion of```
man chmod
```
hi
do you see the chmod in my post ??? --> [COLOR=Red]chmod 1750[/COLOR] !!!!!!
cheers

---

### Post by bab1 on 2013-02-15
> **rnerwein said:**
> hi
do you see the chmod in my post ??? --> [COLOR=Red]chmod 1750[/COLOR] !!!!!!
cheers

Of course I saw your post.  I think you need to read my post a little more carefully.  What I'm saying is the sticky bit is not needed in your permissions scheme.  The permissions 0750 and 1750 both work the same as you have no world writable permissions as there is in the /tmp directory.  

*The sticky bit is for users **[COLOR="Red"]not[/COLOR]** in the group or the owner of the file **[COLOR="Red"]but do have rw rights to the directory[/COLOR]**.*  Once again:  Look at your own reference to the /tmp directory and read up on the Linux sticky bit a little more.

---

