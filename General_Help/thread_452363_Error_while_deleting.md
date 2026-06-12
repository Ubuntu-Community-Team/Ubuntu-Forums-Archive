---
title: "Error while deleting"
date: 2007-05-23
forum: General Help
---

### Post by liberalist on 2007-05-23
Hi everyone, 

I get an error while I try to delete a file from the garbage bin. I checked the permissions and it is read, write and execute for the owner (file group: myusername).  A reboot of the system did not help either.

Attached is the error window.

How can I solve this? 

Thank you very much in advance.

PS: In Mac OS X, I could do a "force empty trash". Is the same possible on Linux?

---

### Post by atoponce on 2007-05-23
The error says that you do not have permissions on the parent folder to make such an action.  Have you checked those permissions?

---

### Post by veerakumar on 2007-05-23
You don't have neccessary permissions for /home.
You may have permission for subdiectory like /home/etc/*
but not for /home.
There is the problem.
Do su root
rm -f /home/file


Thanks

---

### Post by liberalist on 2007-05-23
I did:

```
sudo rm -f /home/file 
```

but with no success. I looked in the directory I cannot throw away and I see all kinds of lock symbols, how can I get rid of them? I tried changing the permissions, but I couldn't.

---

### Post by adn258 on 2008-04-09
> **liberalist said:**
> I did:

```
sudo rm -f /home/file 
```

but with no success. I looked in the directory I cannot throw away and I see all kinds of lock symbols, how can I get rid of them? I tried changing the permissions, but I couldn't.

I AM HAVING the same problem to dang it what do we do?

---

### Post by JustinJS on 2008-05-04
bump because im having the same problem

---

### Post by Adrastos on 2008-05-25
The error says that you do not have permissions on the parent folder to make such an action.You can change the permissions if you have logged in as root.
You try this

> 
sudo nautilus

then browse for the folder in this new window and delete the files.
It worked for me.

---

### Post by oliviacond on 2008-05-25
did not work for me.
after i empty the trash using "sudo nautilus", the file is still there.
it seems like it only delete the root's trash, not user's trash.

---

