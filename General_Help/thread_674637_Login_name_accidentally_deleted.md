---
title: "Login name accidentally deleted"
date: 2008-01-21
forum: General Help
---

### Post by DapperMe17 on 2008-01-21
Kubuntu 7.10

I accidentally deleted my "login" name from the User configuration file in System Settings. 
Now, any login attempt fails.


I was able to create a new user via recovery mode, however, my original root password isn't recognized when I try to update in Administrator Mode in the System Settings.


Anyone help me get my original user name back?


Thanks!

---

### Post by bodhi.zazen on 2008-01-21
Boot to recovery mode again, add your new user to the admin group.

IMO the easiest way to do this is to directly edit /etc/group

```
nano /etc/group
```

Add your new user at the end of the list on the admin line.

Alternately, make a new user with the old user name, but you need to be cautious. Is you old home still there or has it been deleted ?

---

### Post by DapperMe17 on 2008-01-21
In recovery mode, I "sudo nano /etc/groups"....where the list already includes my original user name(ex.. clark)", as well as the new user (ex...clark1). So, it appear as if it is already there??? 

Maybe I'm not doing it right?

---

### Post by bodhi.zazen on 2008-01-21
Sounds like you are using KDE ?

I am not certain what may be the nature of your problem, but in /etc/group, just add you new user to the admin line, comma dilineated, and you should be able to reboot and enter administrative mode and fix the problem.

Another option is to boot to the recovery mode and start x with :

```
startx
```

---

### Post by DapperMe17 on 2008-01-22
Yes, I'm using KDE. 

Your instructions are boot from Recovery mode, "sudo nano /etc/group", then.....I see a list of all kinds of stuff. I see an "admin" entry, as well as both usernames (clark & clark1). 

I'm confused on your directions from this point...



PS...After previously adding a user (Clark1) from the Recovery mode, I'm able to see two Users to choose from at the sign-in page. The original (Clark1), which actually shows now as the name description of ClarkKent(which is the name description for the original username of Clark). This is the login that continues to give me the 'login failed", when I enter the original username & password. If I leave the username blank & enter the password, I don't get "...failed", instead X just recycles back to the KDE login page.

I am able to login to KDE with the new user (Clark1), but then cannot enter the "administrator mode" under system settings, in order to put back the original user name...

---

### Post by bodhi.zazen on 2008-01-22
OK

Two suggestions, to enter the administrative mode, use the password of your second user.

If that fails, go back to recovery mode and enter :

```
startx
```

That should start kde (you can try startkde if startx fails).

From there you should be able to enter administrative mode with no problems (as you are running as root).

---

### Post by DapperMe17 on 2008-01-22
Thanks, that worked!

---

