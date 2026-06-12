---
title: "Have to reset my password on every boot"
date: 2006-11-22
forum: General Help
---

### Post by cbf305 on 2006-11-22
Hello all,

I have a weird password problem with Edgy.  I searched the forums, but didn't find anything close.  My upgrade from Dapper went perfectly.  All my Beryl eye candy is running fine.  About 2 weeks ago the Update Manager asked me to upgrade some stuff, I let it.  It was early in the morning and I wasn't fully awake so I didn't get a good look at what it upgraded.  Ever since then each time I turn on my computer I have boot into safe mode and reset my user password.  I "init 5" and login to X without a problem.  Once I am in X I no longer can use my password to start any admin tasks.  I can't even reset my password from the console.  If I reboot I have to go into safe mode and reset my password again, or else I won't be able to login.  I have been using Linux for about 5 months now, but I have not encountered anything in the authentication department yet so I don't quite know where to start troubleshooting.  Can anyone lead me in the right direction?

Thanks
John :-)

---

### Post by cbf305 on 2006-11-22
I figured it out.

I was playing with passwd at the recovery console and I tried deleting the password for my user account.  The I set the password again.  That seems to have cleared out whatever was causing the problem.

Thanks,
John :-)

---

### Post by HeatPro on 2006-11-22
I was running Dapper for the past year with no troubles.
After yesterday's 12 upgrades, I could no longer log in.
After entering my name and password, the screen returned to the login.
Fortunately, I had downloaded the Edgy 6.10 image yesterday,
 so I installed it.
Lost some emails and stuff, no big deal; but
It sure is fishy to make an upgrade that makes users have to reinstall.](*,)

---

