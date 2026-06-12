---
title: "iDrive online backup for Linux"
date: 2013-09-10
forum: General Help
---

### Post by Rooster2000 on 2013-09-10
I noticed from some old threads that some were wishing iDrive to support Linux platforms as well. Didn't notice that anyone would have posted about it, iDrive has published some time ago a command line utility and scripts with which you can do your online backups in Linux environment.

[https://www.idrive.com/online-backup-linux.htm](https://www.idrive.com/online-backup-linux.htm)

I downloaded the utility and scripts and tried to do some basic things, like configuring or validating my account, but I keep having the error messages that my username or password is incorrect. I wonder if this has something to do with the fact that I created and used my account to backup my WinXP, and this account still contains some files backed up from XP.

Anyway, if I try to validate my account now from my Lubuntu 13.04, I get

```

$ ./idevsutil --validate --user=<username>
Password: 

<tree message="ERROR" desc="Invalid username or Password"/>


Unable to reach the server; account validation has failed

```

even though the same username and password lets me log in into my account on their web page.

Has anyone tried these scripts and command line utility and got backups running successfully?

---

### Post by bkline on 2013-09-10
I believe the use of the API is only supported for accounts created after 2011-11-23.  If your account pre-dates that cutoff, you may need to create a new account.  See, for example:

[http://forum.idrive.com/topic.php?id=24](http://forum.idrive.com/topic.php?id=24)

---

### Post by Rooster2000 on 2013-09-14
Yes, that seems to be the reason, my account was created pre-2011-11-23.

I created a new account and got connection successfully through API interface. 

Thanks for help!

---

