---
title: "Prevent owner:group From Changing?"
date: 2019-06-29
forum: General Help
---

### Post by rebeltaz on 2019-06-29
I have an external USB drive that I run through a raspberry pi. I have all of the files set so that the owner:group is me - derek:derek

However, if I shut the pi down and plug that drive into my main computer, for some reason, every file changes to 1001 for the owner and either 1001 or  piavpn shown as the group. I have to manually run [chown -R derek:derek] on the whole drive to be able to access it on the main system. Then, when I put it back in the Pi, some of the folders forget who owns them and I have to run that chown command again. 

Is there anyway to tell the drive to not let anyone change the owner:group?

---

### Post by HermanAB on 2019-06-29
The owner:group is a number.  The number is matched to a name on the machine that you plug the drive into.  So if the Pi user is JoePlumber with UID 1001, while the user on the Ubuntu is JaneDoe with UID 1001, then the owner will seem to change from JoePlumber to JaneDoe when you move it around.  The number is however unchanged.

---

### Post by rebeltaz on 2019-06-30
When I set up the Pi, though, I set it up so that the username:group and password of the one account associated with that system is the exact same as the one on my main system - derek:derek. So since on both system derek:derek is the only user:group, shouldn't that 1001:1001 equate to the same user:group on both machines? Or am I missing / not understanding something (quite possibly)?

---

### Post by CatKiller on 2019-06-30
On Ubuntu the first user created is user 1000. On your pi there may already have been a user 1000 set up before you created your user, or it may have started counting at 1001. It's a pretty arbitrary configuration. There may well be a way to create a user with a specific number, but it's not something I've ever played around with.

---

### Post by kpatz on 2019-06-30
Run the command **id** from a shell on both your Pi and your other system you use the drive on (I'm guessing an Ubuntu system since you're posting here)

On one you'll probably see something like: ```
uid=1000(derek) gid=1000(derek)...
```

And on the other you'll see something like: ```
uid=1001(derek) gid=1001(derek)...
```

You may be derek:derek on both systems but their uid/gid is different.  If you look at the file /etc/passwd on both systems, you'll see the users and their uids.  There are ways to change your UID, but it gets a little involved.  You'd have to edit /etc/passwd, /etc/group, /etc/shadow, and chown your home directory and the files/directories on the external drive.  It gets a little more complicated if uid 1001 and 1000 are both in use on both systems.

On Ubuntu, you can create a user with a specific UID by using **adduser --uid XXXX YYYY** where XXXX is the uid and YYYY is the username.  You could create a new user on both systems with the same UID this way (use something like 2000 to ensure it's not taken, or check /etc/passwd on both systems first).  I don't know if this command is supported on the Pi's version of Linux, but there is probably something similar like useradd that would work.

---

### Post by rebeltaz on 2019-07-04
I won't be back in the shop until Friday (Independence Day and all) so I will check that out then, but I wanted to reply now. I don't get emails telling me that there are replies, so I quite often miss them. I didn't want you to think that I was ignoring you. 

Other than creating new users on both systems, is there any way to force the drive to mount on the main system (yes, Ubuntu 18.04) in such a way that all of the same owner:group and settings will be retained as when it's mounted on the Pi?

Thanks for the information.

---

### Post by HermanAB on 2019-07-04
Well, the point that we are trying to make is that the drive data IS the same.  It is the interpretation thereof on the two machines that is different.

If you want the users and groups to be identical on all machines, then you need to set up a Network Information Service such as Yellow Pages.

Read 'man yp' for details:
[https://man.openbsd.org/yp](https://man.openbsd.org/yp)

---

### Post by rebeltaz on 2019-07-08
I thought I responded to this, but I don't see it. Thank you all for your help. I will definitively read over all of this. 

One last question, if I may... does it hurt anything to just run a recursive chown on all the files when I swap from one system to the other? Other than it being a pain?

---

### Post by HermanAB on 2019-07-08
You can chown as many times as you like.  It is just data.

However, after the second time, it would have been less work to change one machine so that the two systems use the same UID:GID numbers.

---

### Post by rebeltaz on 2019-07-11
I will look into that - changing the uids - thank you for all your help!

---

