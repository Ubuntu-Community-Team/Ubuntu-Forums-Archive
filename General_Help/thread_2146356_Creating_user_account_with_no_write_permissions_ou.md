---
title: "Creating user account with no write permissions outside home directory."
date: 2013-05-18
forum: General Help
---

### Post by clungzta on 2013-05-18
Hi,
I'm newish to Ubuntu.
I would like to create a Guest account on my machine so that my freinds can read the whole filesystem over public FTP/SSH, but can only write to they're own home Directories.

I'm using: 
Regular Ubuntu 12.04
Openssh Server
VSFTPD Ftp Server
Static IP Adress

All the services are running properly, I just need to set up the limited accounts.
I've found this [https://help.ubuntu.com/12.04/serverguide/user-management.html](https://help.ubuntu.com/12.04/serverguide/user-management.html) I've got a basic Idea, but don't know how to get exactly what I need to do for my situation.

Can someone please help?

Cheers,
Alex :)

---

### Post by prodigy_ on 2013-05-18
You can create regular accounts for them. Just make sure they're [NOT in **sudo** or **admin**](https://help.ubuntu.com/community/RootSudo#Allowing_other_users_to_run_sudo) groups. That's the easiest way (since you don't have to anything special). They'll be pretty much confined within their home directories (unless you have a directory or file system with [write permission granted to everyone](http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) somewhere).

However, if you really need to restrict access for a user, you'll have to do some research about restricted shells.

---

