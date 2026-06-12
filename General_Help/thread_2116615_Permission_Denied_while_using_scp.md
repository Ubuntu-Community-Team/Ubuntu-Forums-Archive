---
title: "Permission Denied while using scp"
date: 2013-02-16
forum: General Help
---

### Post by IVIax94 on 2013-02-16
Hey guys,

I'm trying to use Ubuntu for my programming class. Generally, I would use Windows with PuTTY and XMing, but I really like Sublime Text and thus decided to install it in Ubuntu. When I try to use the scp command to copy the project directory to my computer, I get the error "/home/max/: Permission denied". When I throw a sudo in front of the command, I get "sudo: must be setuid root". I took ownership of the /home/max/ directory using "chown max /home/max/, but I still can't copy. My scp command is "scp -r 'myusername'@login.engin.umich.edu/'project directory' /home/max/".

Can anyone help me out? Thanks!

EDIT: I'm pretty sure my problem was that I was logged into the server, and thus the /home/max/ directory doesn't belong to me (or exist). Therefore, I think I need to do the whole username@hostname thing for /home/max/. However, max@ubuntu didn't work for this (that's what some googling told me to do). How do I do this correctly?

---

### Post by Doug S on 2013-02-16
Hi, and welcome to Ubuntu forums.
 
I'm not sure I understand your issue. I'll just describe what I would do:
 
In a terminal window on my Ubuntu computer, I would make a temporary directory for the incoming files:```
doug@s15:~$ mkdir class_project
doug@s15:~$ cd class_project
doug@s15:~/class_project$

```Then use scp to copy the project:```
scp -p -r [EMAIL="myusername@login.engin.umich.edu:/'project"]myusername@login.engin.umich.edu:/'project[/EMAIL] directory' ./
```Hope this helps

---

### Post by Impavidus on 2013-02-16
In a shell running on your local computer (the one you're copying to) use```
scp -r username_on_server@server:/path/to/project/ ~/local/directory/
```It will ask you for your password on the server. Watch that colon, it was missing in your command as you wrote it. Not sure what the effect would be. If you omit the first slash, it will assume you specify the path relative to your home directory on that server.

---

### Post by gordintoronto on 2013-02-16
Can you include your scp command in your message?

Personally, I would carry my files around with me on a flash drive, and use Nautilus to move them around.

---

