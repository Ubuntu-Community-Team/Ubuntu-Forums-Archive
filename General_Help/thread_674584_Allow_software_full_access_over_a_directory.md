---
title: "Allow software full access over a directory"
date: 2008-01-21
forum: General Help
---

### Post by werg on 2008-01-21
Hi, I need a software to be able to write and erase within a certain directory so that it can function properly. How to I authorize it?

Thanks

---

### Post by leonidas666 on 2008-01-21
If you are running a cli programm, prefixing the command with sudo will give the programm access to all your system. Use 
```
man sudo
```
to find out more about sudo.You can start gui programms by using gksudo or kdesu, depending on whether you run gnome or kde.

What exactly do you want to do?

---

### Post by nemilar on 2008-01-22
If the program runs as a specific user (e.g, apache runs as the user www-data), you can change the ownership of that directory to that user, and grant it access rights.  Or, you can use groups to do the same thing. 

It would be helpful to know more about your unique situation, but here's an example for apache:

If you need apache, running as user www-data, to be able to access and write the directory /var/wwwdocs/, you can do:

chown www-data /var/wwwdocs -R
chmod 755 /var/wwwdocs -R

the chown command changes the owndership, -R meaning recursively
chmod 755 grants read, write, and execute permissions for the owner (www-data), and read/execute permissions for the group and all other users.

Hope this is helpful!

---

### Post by werg on 2008-01-23
> **leonidas666 said:**
> If you are running a cli programm, prefixing the command with sudo will give the programm access to all your system. Use 
```
man sudo
```
to find out more about sudo.You can start gui programms by using gksudo or kdesu, depending on whether you run gnome or kde.

What exactly do you want to do?

I have this program that needs to create directories and save files within certain locations. The problem is, that program doesn't have the necessary access rights. All I want to do is give the program the authority to do so.

---

