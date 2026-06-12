---
title: "Log in to x as root"
date: 2007-04-26
forum: General Help
---

### Post by Dave_is_sexy on 2007-04-26
i've clicked on every google result for 5 pages and the responses are just "there's no need to do that".

Tell me!

---

### Post by Turellius on 2007-04-26
No, there is no need to do that.  If you use the GUI then it will simply ask for the password if you try to do something that needs root permissions.  Also, if you use the terminal and need to issue one command as root then just type 'sudo' before whatever command you need to execute, and as always you can use su to elevate your terminal session to root privileges, but I bet there are people on this forum that would advise against that.  Anyways, hope that helps.

---

### Post by newyorkcityjay on 2007-04-26
When I try this I get asked for a password - I try my normal password, but nothing.  I just installed Feisty Fawn tonight.

---

### Post by alogon on 2007-04-26
I was also not able to get in as root using the password I installed with. The easy solution is to `sudo passwd` then type in your user password. Then enter what you would like your new root password to be press return and type in the new root password a second time.

This is if you want to set your root password. This will not help you run X as root.. there really is no need to do that.

---

### Post by aysiu on 2007-04-27
Try this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

