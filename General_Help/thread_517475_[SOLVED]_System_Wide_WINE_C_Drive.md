---
title: "[SOLVED] System Wide WINE C Drive"
date: 2007-08-04
forum: General Help
---

### Post by Vince4Amy on 2007-08-04
As today I finally got round to erasing Windows. I'd like to install WINE Again, but how would I go about doing this so that the fake C Drive & WINE Apps are system wide?

---

### Post by apswartz on 2007-08-04
I'm not sure of what you mean by systemwide, but you can always set up a link in your Wine C: drive...
```
ln -s target linkname
```

For example
```
ln -s ~/documents documents
```

---

### Post by Vince4Amy on 2007-08-04
I mean so every user can access it. Obviously if it's /home/myusername/.wine/drive_C no other users will be able to run WINE apps without reinstalling on each & every account.

---

### Post by avik on 2007-08-04
Here's an unofficial solution.  Let's pretend you have a bunch of users name user1, user2, usr3, etc.

Decide which user will keep the actual files; it doesn't matter who does it, but let that person set up WINE.  We'll pretend it's user1.

Then, for all the other users, create a symlink to user1's .wine directory:

```
ln -s /home/user1/.wine /home/user2/.wine
```

Log on to each user and create a symlink for each user, always pointing to user1's .wine directory.  That way, WINE will think each user has a .wine directory, when it really is just user1's .wine directory being shared.

And make sure you give that directory permission to be modified by any of the users.

---

### Post by apswartz on 2007-08-04
Good idea avik. I think to make it work you will need to give the user's home directory world readable privileges or group readable permissions if all are in the same group.

Perhaps a tweak to your idea. Create a dedicated directory, e.g., /home/wine/.wine to link everybody to.

---

### Post by Vince4Amy on 2007-08-04
Yep thanks, right i'll make a new directory specifically /home/wine. I'll report back on what happens. Thanks.

Edit: Thanks It Worked. Thanks A Lot.

---

### Post by www.rzr.online.fr on 2008-05-16
What about using union fs to merge users's files over system files ?
-- 
[http://rzr.online.fr/q/wine](http://rzr.online.fr/q/wine)

---

