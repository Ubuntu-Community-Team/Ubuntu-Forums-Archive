---
title: "Easy way to LAN backup (Automatically)? without Password Authentication?"
date: 2015-09-25
forum: General Help
---

### Post by 777funk on 2015-09-25
My wife recently lost some data due to a failed HDD. I'm partially responsible for this. So... now I'm helping her to not have this problem again. I'd like to backup her data on my machine over the network. 

They're both Ubuntu boxes. Is there an easy way to do this without SSH Auth? OR should I say without being present and running backups manually. I'd like to chron it and have it go automatically.

That part isn't a problem. I like LuckyBackup as a nice graphical to RSync but I don't know how to get it to work without starting it from a terminal (which prompts for the password on the server machine).

---

### Post by TheFu on 2015-09-26
Setup ssh key-based authentication [https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server) and use something without a GUI if you want it to be automated by cron.  I like rdiff-backup for this - it can pull or push backups.
[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/)

If you use root on both sides for this, you can create complete system backups. Without root, owner, group, and permissions will be lost. If you use root for this, be certain to lock down the account.

Don't fear ssh - it is the swiss-army-knife of Unix-to-Unix connectivity.  The list of things that can be accomplished with ssh is amazing. [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

---

