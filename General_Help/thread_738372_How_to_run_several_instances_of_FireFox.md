---
title: "How to run several instances of FireFox ?"
date: 2008-03-28
forum: General Help
---

### Post by tounano on 2008-03-28
Hi,

I got my new EEE PC, and installed xubuntu on it. I have a need of running several instances of FireFox.

What I used to do in WinXP is to create several different users and run firefox with "RunAs" command (It's the same as sudo in ubuntu). After I did it, I had my Foxes runing, using different settings each.

I tried the same trick under my ubuntu and it won't worked - "sudo -u [otheruser] firefox". I also tried some more variations of this trick, but had no luck. I always get
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:10269): Gtk-WARNING **: cannot open display: 
``` 


Do you have any suggestion for how to solve this little problem? Or just run several FF instances with different profiles?

Thanks.

---

### Post by gaussian on 2008-03-28
The problem here is that your other users don't have permission to connect to the X-session you are running. This can be fixed with granting them that permission. Tools like xauth come to my mind, I have not done this in a while though.

---

### Post by kellemes on 2008-03-28
sudo has nothing to do with "running as user".. sudo is explained here.. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

To run firefox as a diferent user you make use of profiles..
You can start the profilemanager of firefox like so..
```
firefox -profilemanager
```
Here you can create different profiles..

To start Firefox using a specific profile you can do the following..
```
firefox -P <profilename>
```

---

### Post by tounano on 2008-03-28
Hi,

Thanks for the reply, I also tried the trick with the profiles, but it don't work, because it can handle only one profile instance. That's the reason why on windows I am using the "runas" command.

I'll try the permissions advice.

anyway, do you have any other suggestions?

---

### Post by kellemes on 2008-03-28
> **tounano said:**
> Hi,

Thanks for the reply, I also tried the trick with the profiles, but it don't work, because it can handle only one profile instance. That's the reason why on windows I am using the "runas" command.

I'll try the permissions advice.

anyway, do you have any other suggestions?

Don't see what's the issue here..
I have created 3 profiles and can run them all 3 at the same time..
I have 3 instances of firefox running without problem.

---

### Post by tounano on 2008-03-28
I don't know how you managed to do it, but it doesn't work for me. I created 2 users. and when I run firefox -P user1, and just after it runs firefox i run firefox -P user2, it runs my 2 instances of firefox under the profile of user1.

However, after I quit firefox and run firefox -P user2, it launches FF with user2 profile.

Any other ideas?

---

### Post by kellemes on 2008-03-28
> **tounano said:**
> I don't know how you managed to do it, but it doesn't work for me. I created 2 users. and when I run firefox -P user1, and just after it runs firefox i run firefox -P user2, it runs my 2 instances of firefox under the profile of user1.

However, after I quit firefox and run firefox -P user2, it launches FF with user2 profile.

Any other ideas?

Well.. not really.. ;-)

I just tested like so..
```
firefox -profilemanager
```
Here I create userfirst **and** usersecond.
Now I run..
```
firefox -P userfirst
```
I personalized this profile by selecting a startpage, so I know this is userfirst when it's started

Same thing for usersecond..
```
firefox -P usersecond
```
Another startpage that proves to me it's usersecond..

Now when I do the following I get two instances.. (&=to close the commandline in the terminal)

```
firefox -P userfirst &
firefox -P usersecond &
```

---

