---
title: "usermod woes"
date: 2013-01-19
forum: General Help
---

### Post by cackles on 2013-01-19
I added a user with no home dir thinking when they logged on they wouldnt be able to see or do anything, I was wrong.

So I used 

```
usermod -d /new/dir/here username
```

Now when logging in using that username I get

```
/usr/bin/xauth:  timeout in locking authority file /new/dir/here/.Xauthority
```

How can I correct this?

Also how do I restrict that user to that folder only?

Easiest way, I think, is to delete the user and start again but Id like to know how to fix it.

I checked in the /etc/passwd and it shows the home dir for the user to be what I set it at.

---

### Post by CaptainMark on 2013-01-20
Perhaps its permissions of the .Xauthority file in the new home folder, my is 600, check yours is the same, what exactly are you trying to achieve?

---

### Post by cackles on 2013-01-20
Basically just a user with a new home directory and them to be restricted to that dir.

---

### Post by CaptainMark on 2013-01-20
a standard user will only have write access to their own home folder, they must has read access to other files or you could not run the system at all with that user.

if you mean to make it so new users cannot read your home directory just create a normal user in the standard way, and use ```
chmod o-r ~
```to block read access to all other users, you don't need to place their home folder anywhere special

---

