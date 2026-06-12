---
title: "Cant change my permissions -please help"
date: 2007-05-24
forum: General Help
---

### Post by Zavie A. on 2007-05-24
i recently deleted Windows XP and installed Ubuntu Feisty Fawn. And everything was wonderful until just now.

I tried to delete some old programs on my second drive that don't work with Ubuntu and were just taking up space and its telling me i cant do this because i don't have "permissions' 

[COLOR="Red"]IS THERE ANY WAY FOR ME TO CHANGE THE PERMISSIONS OF A FILE?[/COLOR]

im almost in tears...PLEASE HELP!

---

### Post by spin2cool on 2007-05-24
I think you need to read a little bit on linux permissions, so that you understand what they are and how to work with them.
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

The problem is likely that 
a) your user doesn't own the file  and/or
b) your user doesn't have permission to access the file.

These problems can be fixed with commands like
sudo chown username:username filename
sudo chmod u+rw filename

---

### Post by tomcheng76 on 2007-05-24
is your second drive using NTFS filesystem?
if it is true, then you probably only have read access right to that drive
it it is not, then you can try
chmod u+w filename (it means add the write right for the user to that "filename" file)

---

### Post by Zavie A. on 2007-05-24
Lol...i have a basic understanding of how permissions work. (but i read the page...very informative, thank you :) )

And i believe the problem is that i no longer OWN the file...

and yes my second drive uses an NTFS filesystem.

BUT: new problem, i type in "sudo chown username:username filename" (with my correct username and filename) and it says that it cannot access it as it does not exist...

---

### Post by spin2cool on 2007-05-24
installing NTFS read/write support;
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

