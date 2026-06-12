---
title: "creating network users?"
date: 2006-08-31
forum: General Help
---

### Post by cykematica on 2006-08-31
hey guys, i know that i've found this answer on here somewhere before, but i can't find it now.  i am networked to some windows machines, and i installed samba to share to them.  i need to set up user accounts on ubuntu for them, but i don't want them to be able to have local access to login to my computer.  i know i set shell to be /dev/null, but what do i set the home directory to be?  and also, i forget the samba commands to make them a samba user.  thanks :)

breakdown

---

### Post by Ramses de Norre on 2006-08-31
I guess you can give them anything you want as home dir.. name it samba or something. It doesn't matter because they wont log in to your system.

Then add the usernames to /etc/samba/smbusers and run ```
sudo smbpasswd -a username
``` to set a password.

---

