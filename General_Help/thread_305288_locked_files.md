---
title: "locked files????"
date: 2006-11-23
forum: General Help
---

### Post by crashtestway on 2006-11-23
ok i an up and running with ubuntu sweet free of the windows bug:) o some how locked file on one of my folders and can't unlock it?????](*,)  how do i do i undo that???? also looking for some basic fps for ubuntu that are maked for ubuntu or that will run great in wine-hq i am new so be easy on me
thanks again for a great o/s ! ! !


james d
columbus ohio usa

---

### Post by adwait on 2006-11-23
What do you mean by you locked it??

---

### Post by crashtestway on 2006-11-23
[http://img241.imageshack.us/img241/9822/screenshotyj4.png](http://img241.imageshack.us/img241/9822/screenshotyj4.png)


thats what i did...somehow????:confused:

---

### Post by adwait on 2006-11-23
I think its some permission issue, but I am not using GNOME so I don't really know what that lock icon means. Could you post the output of
```
ls /home/<username>/
```

---

### Post by crashtestway on 2006-11-23
i am the only user,only one user id? i think i broke it lol??? is there a way i can enter my password and reset the files? i can't move or delete them???](*,) ](*,) ](*,)

---

### Post by adwait on 2006-11-23
Yes, so you seem to have somehow changed their permissions. If you would post the output of the command above, I would be able to understand the problem (perhaps). You can enter the command in the terminal window which can be found under Application>Accessories>Terminal.

---

### Post by kerry_s on 2006-11-23
Try launching root nautilus->
alt + F2 > gksu nautilus
then right click the files > properties> permissions & change them to your user in the drop down list.

---

### Post by thingy on 2006-11-23
Yes! As adwait said...it is simply the case that the folders and files with the locked icon have only read only access for the user you were logged in as.
 
A simple fix would be to give the user who owns the folders and files, read/write access...
 
e.g.
 
chmod u+rw file1 file2 file3 etc.
 
or to do a bunch of files at the same time **(be very careful when using wildcards)** you can do this:
 
chmod u+rw *.doc *.txt *.tif etc
 
If it turns out that the you are not the owner of these files or folders, then you need to make a decision on either changing the ownership of the files/folders to yourself or to give group/other people read/write permissions on the files.
 
Option 1. Taking owener ship of the files
 
chown username.username file1 file2 file3 etc.
chown username.username *.txt *.doc
 
Option 2. Giving rw permisions to group AND others
 
chmod og+rw file1 file2 file3 etc.
 
Here is a good page which explains file permissions. [[link]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")]
 
Definitely read it as it is important that you understand file permissions in linux for security reasons.

---

### Post by crashtestway on 2006-11-23
kerry_s you rock ! ! ! it did it sweet..... thanks for all the help guys:P

p.s. i want to buy like a few buck to ubuntu how do i do that paypal ?? check??? what is best?.... moneyorder?????:KS :mrgreen:

---

