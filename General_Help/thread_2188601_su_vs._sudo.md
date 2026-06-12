---
title: "su vs. sudo"
date: 2013-11-18
forum: General Help
---

### Post by dannymichel on 2013-11-18
I noticed that things were messed up when i installed apache php and mysql using su, but they were fine when i used sudo. What's the reason behind that?

---

### Post by Topsiho on 2013-11-18
You don't tell what you mean with "messed up".

Usually in Linux you use the computer as a normal user, with restricted privileges, so you can't mess the system up. When you have to change the system, however, you need root privileges, and obtain these with su, and then giving the special root password. You then have these privileges untill you exit as root, or untill you shut off the computer. Brrrr....

In Ubuntu this is different. In Ubuntu, if you need root privileges, then you use sudo, giving your password, that was typed in during the install. You then have root privileges for only one command, or during a restricted time. This causes that you *** are not having these root privileges all the time you are using the computer***, putting your system at risk, or making it more vulnerable for attacks from outside.

So Ubuntu is safer to use then the other Linuxes :)

Topsiho

---

### Post by texpat on 2013-11-18
And elaborating on what Topsiho said, this means that with su you become root, so any installs you do go to the root user/account. So probably settings and other application data go to /home/root instead of /home/yourname... Conversely with sudo your user gets root priviliges but anything you install still goes to /home/yourname.

---

### Post by ajgreeny on 2013-11-18
See the link in my signature for all the details on RootSudo.

Using **su** in ubuntu will not get you anywhere.

---

### Post by Lars Noodén on 2013-11-18
sudo is quite useful once you get more familiar with it and start configuring sudoers.  There is a lot of material online.  There is also a new book:

[https://www.michaelwlucas.com/nonfiction/sudo-mastery](https://www.michaelwlucas.com/nonfiction/sudo-mastery) 

I haven't read that particular one yet but his others have been useful and well-received.  Apparently you can even log and replay sudo sessions.

---

