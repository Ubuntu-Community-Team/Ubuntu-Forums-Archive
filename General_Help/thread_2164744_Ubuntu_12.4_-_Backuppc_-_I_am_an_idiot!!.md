---
title: "Ubuntu 12.4 - Backuppc - I am an idiot!!"
date: 2013-08-01
forum: General Help
---

### Post by TechMansoor on 2013-08-01
Hello. First and foremost I am an idiot and worthless, so you guys will need to think of me as such while helping me troubleshoot.

In any case...

I have a raid 10 server I'm running in which I have installed ubuntu server with a full disc(999gb) lvm guided install.

Upon doing this I did the typical:

sudo apt-get install backuppc

Everything goes well.

I know for a fact. Apache, Samba, as well as of course backuppc is installed.

Yet I can't get to: [http://ip/backuppc](http://ip/backuppc).

I get a:

"The requested URL /backuppc/ was not found on this server."

My question to this community is where do I begin to troubleshoot. Again you have to talk to me like I'm an idiot and don't know nothing. I am not a noob as I've been dealing with Linux for years, but I might as well as be. 

Thanks

---

### Post by newbie-user on 2013-08-02
Create a virtual host in apache that points to wherever the backuppc folder is located.

Or

Symlink the backuppc folder to the /var/www directory. This is probably much easier.

---

