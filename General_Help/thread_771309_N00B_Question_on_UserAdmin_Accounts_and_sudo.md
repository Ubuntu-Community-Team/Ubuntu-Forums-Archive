---
title: "N00B Question on User/Admin Accounts and sudo"
date: 2008-04-27
forum: General Help
---

### Post by igfud on 2008-04-27
Hello,

I need to run the following command in order to use my VPN client:

```
sudo /etc/init.d/vpnclient_init start
```

I'm not going to use the program very regularly, but I don't want to have to log in as an admin, run the command, switch users, and then use the Internet.  Is there harm in giving my user account the ability to run sudo commands?  Is it true that I should *only* use the administrator account for admin purposes, and a user account for everything else?  I guess I heard that a part of Ubuntu security is to only use the admin account for admin purposes which requires switching users each time I want to install a program or update.  I've been doing this for about a year now and I just want to make sure I'm not causing a bunch of unnecessary hassle for myself.

If it is true that I should only use a user account for day to day use, what is the best method of running the VPN sudo command?  Is there a way I can add it to the startup processes, or is there another method of accomplishing this?

Thanks,
igfud

---

### Post by ryanhaigh on 2008-04-28
Ubuntu is setup so that you have a user account which can use sudo to admin or other tasks that require root access. You do not need to have two accounts, you just use sudo only when you need to.

---

### Post by pbpersson on 2008-04-28
If you wanted to know how to have the system automatically run a shell script in the background every time you start the machine, try Googling the following:

ubuntu "shell script" startup

However, the articles I saw seemed to be way beyond NOOB talk so I don't know if you want to head down that road.   :confused:

OH.....additionally.....running something using sudo and supplying a password file so you don't need to always type the password might be accomplished....perhaps.....go to a console prompt and type "man sudo" for more information.

I would THINK there must be an easier way to accomplish this than the leads I just gave you but I have never dealt with this issue before :(

---

### Post by igfud on 2008-04-28
Thanks for the reply!  So I take it there are no "security problems" with using an admin privileged account (i.e. sudo use, Add/Remove Programs, package manager, etc.) for daily activities.

Thanks,
igfud

---

### Post by igfud on 2008-04-28
> **pbpersson said:**
> OH.....additionally.....running something using sudo and supplying a password file so you don't need to always type the password might be accomplished....perhaps.....go to a console prompt and type "man sudo" for more information.

I don't mind running the command in the terminal each time I want to use the program, assuming I can give sudo (ie administrative) privileges to my user account.  I guess I got the wrong impression somewhere that administrative accounts should be used *solely* for administrative purposes. :confused:

Well I guess I won't have to switch account every time I want to run something that requires admin privileges anymore. :)

> If you wanted to know how to have the system automatically run a shell script in the background every time you start the machine, try Googling the following:

ubuntu "shell script" startup


Thanks! I'll check into it.

igfud

---

### Post by mhmjr on 2008-04-28
nm, I misread the OP

---

