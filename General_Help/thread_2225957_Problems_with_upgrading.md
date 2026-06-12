---
title: "Problems with upgrading"
date: 2014-05-24
forum: General Help
---

### Post by frogwarrior on 2014-05-24
I upgraded for the first time (I usually install it fresh) and was lax about backing up my files cuz I thought upgrading doesn't delete anything. Half of the programs I had installed are gone, but what could be a problem (if I hadn't backed the important stuff up) is my /var/www is gone. It can't find it. All my webpages were in there. I haven't reinstalled the LAMP server yet, I don't know if the MySQL databases are gone too. I backed them up too but I mighta missed something. Is the data actually gone, or just located somewhere else? 

A second issue is that I made a new password when I upgraded. The issue is my home folder is encrypted with a different password, so I can't log in automatically with my new password. I have to hit CTRL + ALT + F1 then login through the command line and mount the encrypted home folder by running ecryptfs-mount-private. Then I can log in through the GUI. Is the only simple solution to change back to my old password?

---

