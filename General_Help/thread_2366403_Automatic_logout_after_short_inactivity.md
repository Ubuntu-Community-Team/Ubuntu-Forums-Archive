---
title: "Automatic logout after short inactivity"
date: 2017-07-17
forum: General Help
---

### Post by Coto_Paxi on 2017-07-17
Hi all,

My OS is kubuntu 17.04

After a few minutes of inactivity I am logged out and have to type my password to login again. This is driving me totally banana!

Anyone knows, how I can stop this "automatic madness" (automatic logout)?

Thanks!

---

### Post by BenginM on 2017-07-17
Salutations!

Did you somehow mis-configured or messed-up with xorg .. whatever you did..

if you have a .Xauthority , remove it:

Log into a virtual console tty (Control+Alt+F4) and after typing your username and password:

sudo rm -v .Xauthority

restart the login manger kde or whatever in use:

sudo service lightdm restart

The system should recreate an .Xautority file.

---

### Post by deadflowr on 2017-07-17
Sounds more like it's entering the lock screen, which is typically what happens.
I think you need to set the lock screen timeout in System Settings >> Desktop Behavior.
See: [https://forum.kde.org/viewtopic.php?f=289&t=125371]("https://forum.kde.org/viewtopic.php?f=289&t=125371")

---

### Post by Coto_Paxi on 2017-07-17
Sary.sa, Deadflowr,

Thanks to both of you for your replies!

Deadflowr, your reply solved it! I have waited for some time to check it out and the "automatic screen lock" is now off. Thanks again!

I will mark this post as solved.

Thanks again to both of you!

---

