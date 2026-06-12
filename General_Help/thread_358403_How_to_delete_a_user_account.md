---
title: "How to delete a user account?"
date: 2007-02-10
forum: General Help
---

### Post by Aleksandersen on 2007-02-10
Hi,

How to properly remove a user account and her home directory from the terminal?

---

### Post by meng on 2007-02-10
userdel -r <nameofuser>

---

### Post by Aleksandersen on 2007-02-10
Thanks! That solved it! :)

---

### Post by steve101101 on 2007-02-26
thanks meng. that helped me too.

---

### Post by gdoermann on 2007-12-30
So how do you now add that user again... I just messed up the home folder so I need to be able to delete the user and then add them again.
I used the code: 
```
sudo userdel -r <user name>
```
to delete the user... 
I then used 
```
sudo useradd -r <user name>
```
to try and add the user again (same user name) and it gave me this error:
```
useradd: group <user name> exists - if you want to add this user to that group, use -g.
```
I wanted to delete EVERYTHING that happens when you add a user...
Anyways, so I then tried to delete the group like this:
```
sudo groupdel <user name>
```
and then I added the user again...
```
sudo useradd -r <user name>
```
It didn't give me an error... but it didn't add the user to the menu when I go into the System-> Administration-> Users and Groups.  What else do I need to do?

---

### Post by gdoermann on 2007-12-30
> **gdoermann said:**
> So how do you now add that user again... I just messed up the home folder so I need to be able to delete the user and then add them again.
I used the code: 
```
sudo userdel -r <user name>
```
to delete the user... 
I then used 
```
sudo useradd -r <user name>
```
to try and add the user again (same user name) and it gave me this error:
```
useradd: group <user name> exists - if you want to add this user to that group, use -g.
```
I wanted to delete EVERYTHING that happens when you add a user...
Anyways, so I then tried to delete the group like this:
```
sudo groupdel <user name>
```
and then I added the user again...
```
sudo useradd -r <user name>
```
It didn't give me an error... but it didn't add the user to the menu when I go into the System-> Administration-> Users and Groups.  What else do I need to do?

Ok... so I figured it out.  After you delete the user and the group you can go to the System-> Administration-> Users and Groups and just add the user.  It wasn't working before, I think because you have to delete the group.  (which I had already done with the Users and Groups GUI, but it apparently didn't actually work.

---

