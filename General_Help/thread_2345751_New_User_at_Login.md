---
title: "New User at Login"
date: 2016-12-07
forum: General Help
---

### Post by Quarkrad on 2016-12-07
Running 16.04.  Added 2nd user via Users & Groups - in **Home** I see the two user folders and in each folder there is the usual Desktop, Documents, Downloads, etc folders.  Each user is configured as an Administrator and does not require a password to log on.  When I restart my pc (I dual boot) I press Ubuntu and go straight into user 1 Desktop.   I was expecting to be presented with a window offering me the two users so I can choose which one to boot to.  I can log-off user 1 into user 2 and everything works OK - just keeps booting to user 1 all the time.  This cannot be how it meant to be.

---

### Post by Quarkrad on 2016-12-07
Hmm... this is a clean install of 16.04 this afternoon.  Just changed both users such that they have to ask for their password at login.  Restarted pc and it booted straight into user1 Desktop - appears configuring to have to put in password does not work.

---

### Post by #&amp;thj^% on 2016-12-07
Each user is configured as an Administrator will do this. IE Defaults to the newly added Admin will boot first.
Maybe set one as Custom...as the real Admin & password will let you do anything needed.

---

### Post by Quarkrad on 2016-12-07
I don't have a Custom option - just Admin or Desktop.  I have set user1 as Admin and user2 as Desktop, both having to ask for password.  Still boots to user1 Desktop without asking for user or password.

---

### Post by #&amp;thj^% on 2016-12-07
Hmmm? Your right in saying "This would not be the expected behavior"
And I ran a test just now but I'm using 16.10 and Mate 1.16 as also seen in my Screenshot. And I don't have auto login enabled...but my first user is the first option to boot to.
I wonder if setting your original set-up to auto-login has left a bad side effect.
I'll set-up a new 16.04 Mate and check this out further.
Ill post any findings back here.
Regards
BTW what dose this show now
```
pluma /etc/lightdm/lightdm.conf
```

---

### Post by #&amp;thj^% on 2016-12-07
Ok Now I remember :idea: this was a Bug but I don't have the Link for it ATM....But to disable Auto Login
Open a terminal.
```
sudo -H pluma /etc/lightdm/lightdm.conf
```
It displays some text as follows:

```
[SeatDefaults]  
greeter-session=lightdm-gtk-greeter  
user-session=mate
autologin-user=username
```

This <username> would be your particular user name that is automatically logged in with or without password. Delete this **username** and type in the **administrative username **or leave it blank.
There is other methods also...if this proves to be a bust.
Regards

---

### Post by Quarkrad on 2016-12-08
Wow - that did it, many thanks. I would never have got to that solution without your help.

---

### Post by #&amp;thj^% on 2016-12-08
Your Welcome...glad it worked.
Kind Regards

---

