---
title: "Can't sudo!"
date: 2008-05-08
forum: General Help
---

### Post by mardawi on 2008-05-08
I think this happened when I added a new user, using the Administration> Users and Groups, named 'admin'

After a while, I noticed that all apps that need authentication "gksu" and all other utilities in the Administration menu, crashes after entering the password, and utilities with the new "unlock" button, like the nm-applet, will hang for a while and then display an error, something about permission.

The weird thing that when i use sude in the terminal, it will ask me for my password, will know if i entered it correctly, then do absolutely nothing! not even display a warning message.

I also can't log as root root form tty1.

Can some one please help me? I can't boot from the CD or do a fresh installation since this is a laptop and the CD drive is broken, I can only boot from damn small linux using a USB.

[edit] I can see from Users and Groups that I no longer have; Administer the system, send and receive faxes, use scanners, and use tape drives checked. Can't edit it though

---

### Post by p_quarles on 2008-05-08
You'll need to boot into "recovery mode" first. You can do this by selecting that option from the boot menu, which shows up immediately after the BIOS.

Then, you'll want to check on two things:

1) Make sure that your user is a member of the "admin" group:
```
groups *username*
```
The output should include the word "admin." If it doesn't, type the following command:
```
adduser *username* admin
```

2) Make sure that /etc/hosts is configured correctly. First, get the correct hostname from the computer by typing:
```
hostname
```
Make a note of the output. 

Then, you'll edit the file to make sure that it's correct:
```
nano /etc/hosts
```
The second line should begin with the address 127.0.1.1. Following that should be the hostname you got from the previous command. If it doesn't match up exactly, change it so that it does. 

Now you can restart your computer and boot up normally:
```
shutdown -r now
```

---

### Post by mardawi on 2008-05-08
Worked like a charm!

So it was wrong to create a new user with the name "admin"?

My /etc/hosts file was empty, and i left it so, i remember it was empty before. But everything works now... Thanks a lot!

---

