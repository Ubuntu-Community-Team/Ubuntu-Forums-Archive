---
title: "How to set/change root password"
date: 2007-10-03
forum: General Help
---

### Post by tanveer on 2007-10-03
Hi all,
I just installed ubuntu in my desktop and at the time of installation as far I can remember I only put one password for a user. Now to run system commands when I type with 'sudo command' and gives the users password when asked, it works. My question is isn't there any option to put/change the root password?
Why its taking users password as super users?

---

### Post by anaconda on 2007-10-03
The default user has admin rights. eg. rights to use sudo -command and so rights to do about anything..  and the password is the users who has the sudo rights..

If you want to give root a password then just type (in terminal):
sudo passwd root

but your current user will still have sudo powers after that. Then you could remove your user from the admin group (why?) with editing sudoers file with:
sudo visudo

The default is that root -user doesn't have a password ie. root user is disabled..

---

### Post by tanveer on 2007-10-03
Hi, 
Thanks for your reply. As I am used to redhat where we have a root user and thought similar sort of this in ubuntu. Also facing trouble as everything to do is described in GUI and just found a document where it shows how to install required servers in command prompt with sudo. 
Ubuntu is really cool and I am thinking of installing it in my dell latitude D520 soon.

---

