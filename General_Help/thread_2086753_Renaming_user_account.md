---
title: "Renaming user account"
date: 2012-11-21
forum: General Help
---

### Post by ilmard on 2012-11-21
hello, I've been trying to rename my user for hours now with no luck.

sudo usermod -l new_user_name old_user_name

I get message "user is currently logged in" 

I've also gone into ctl+alt+F1 created a new temp user with sudo rights and when i tried to rename origional user id get the same message about user being logged in. 

I've also tried to kill the user thats supposedly logged in and id STILL get the same message.

i have no idea what im doing wrong. Every single tutorial says to use the usermod code

---

### Post by papibe on 2012-11-21
Hi ilmard, Welcome to the forums ):P

You can't change your own username in a regular session.

You need to boot into recovery mode and do it there. Take a look at this [tutorial]("http://www.psychocats.net/ubuntu/resetpassword") on how to reset your password. Follow it as you were going to do it, but instead of running the password command run the usermod command.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by zombifier25 on 2012-11-22
You can also create a temporary user and give it sudo rights, if you don't want to drop to recovery mode (but I wouldn't recommend this though, it's rather messy):
```
sudo adduser temp
sudo adduser temp sudo
```

Then log out and log in as "temp", and then:
```
sudo usermod -l new_user_name old_user_name
sudo usermod -d /home/new_user_name -m old_user_name # use this command if you want to change the name of your home folder also
sudo ln -s /home/new_user_name /home/old_user_name # some config files will still refer to old home folder. do this to maintain compatibility if you run the above command to change the name of the home folder
```

After that, log in your new user and delete the temp account, along with its home folder:
```
sudo deluser temp
sudo rm -r /home/temp

```

---

### Post by ilmard on 2012-11-23
Thanks for the replies and welcome, That tutorial ended up helping but i messed something up. I had renamed my old user (micheal) to (test). I also changed the /home directory from micheal to test. However when i restarted and got to my login screen it still said Micheal or guest user. I tried to login to Micheal but it wouldnt work. It would accept the password then just go back to the login screen.   I then went back to boot/safemode/root and deleted test/micheal and created a new sudo user. All is well now except for the fact that i still have a user Micheal on my login screen despite the fact that the only user is my current one.

---

### Post by zombifier25 on 2012-11-23
It's possible that only the actual username is changed, not the display name. To change it in Unity, click your name in the upper right corner, chose "User Accounts", click your display name to change it.

(As for the unable to log in problem, it is a completely unrelated issue, and in order to fix it, press Ctrl + Alt + F1, log in and type this command:
```
sudo chown username:username .Xauthority
```
But you seemed to have deleted the account anyway, so you don't need this step)

---

### Post by ilmard on 2012-11-23
> **zombifier25 said:**
> It's possible that only the actual username is changed, not the display name. To change it in Unity, click your name in the upper right corner, chose &quot;User Accounts&quot;, click your display name to change it.

(As for the unable to log in problem, it is a completely unrelated issue, and in order to fix it, press Ctrl + Alt + F1, log in and type this command:
```
sudo chown username:username .Xauthority
```But you seemed to have deleted the account anyway, so you don't need this step)

 Thanks man,  I went into user settings and removed Micheal along with all its files.

---

### Post by ilmard on 2012-11-23
now how would i go about marking this thread as SOLVED??

---

### Post by papibe on 2012-11-23
:) Glad you sorted it out.

[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is how to mark the thread solved.

Regards.

---

