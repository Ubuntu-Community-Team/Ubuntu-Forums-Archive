---
title: "manage users and groups"
date: 2012-12-18
forum: General Help
---

### Post by Pedroski55 on 2012-12-18
I would like a GUI to manage Users and Groups in Ubuntu. I suppose this can be done from the command line, but I am not good at that.

I saw Kuser. Is that the right one to use??

---

### Post by dcstar on 2012-12-19
> **Pedroski55 said:**
> I would like a GUI to manage Users and Groups in Ubuntu. I suppose this can be done from the command line, but I am not good at that.

I saw Kuser. Is that the right one to use??

I just use the System Tools-Administration-Users and Groups tool in Gnome 3.

---

### Post by Pedroski55 on 2012-12-19
Yeah, but ......

I can go to System Settings>User Accounts There I can set User status, ie Administrator or not and Language, that's all. There is nothing to add myself or others to groups. There is such a program in Fedora, where I can add myself to groups, add users and so on. 

That's what I want in Ubuntu.  System Tools does not exist in my version of Ubuntu 12.04

---

### Post by vanadium on 2012-12-19
In Software Center, you can install "Users and groups", which is not anymore installed by default.

---

### Post by shinasha on 2012-12-19
Search for 'users and groups' in the software center and install. I think that is what you are looking for.

---

### Post by Pedroski55 on 2012-12-19
If I do that I get Kuser. Is that what you mean?? Kuser for Gnome??

---

### Post by Morbius1 on 2012-12-19
Are you using Ubuntu or Kubuntu or something else?

If it's Gnome you are using:
```
sudo apt-get install gnome-system-tools
```THen go to the dash thingy or whatever it's called ( I'm an XFCE user :p ) and type in users. It's "Users and Groups" that you want.

If Dash want's you to purchase a book or a movie instead just lauch the utility from the terminal: 
```
users-admin
```

---

### Post by Pedroski55 on 2012-12-19
Thanks. That did the trick. I was already administrator, but not quite properly, according to users-admin. I still can't see how to add myself to groups, but I'll learn the command line for that.

I just want to eliminate possibilities. We have a new Toshiba e-studio243 Photocopier Scanner Printer. Ubuntu correctly identifies it. I downloaded the Toshiba linux driver, a ppd file, and put it in /etc/cups/ppd/ but apart from a click when I say print, nothing happens!

---

### Post by Morbius1 on 2012-12-19
> I still can't see how to add myself to groups, but I'll learn the command line for that.The whole idea of using users-admin is to bring back a gui that can add users to groups. Click on "Manage Groups" then select a group like "lpadmin" for instance. Then select "Add". 

You should be presented with a list of your local users that you want to add to that group.

[COLOR=Blue]**Note**[/COLOR]: If you are one of the users that you are adding to that group you may have to log out and in again for group memebership[ to take affect.

---

### Post by rnerwein on 2012-12-20
> **Pedroski55 said:**
> Thanks. That did the trick. I was already administrator, but not quite properly, according to users-admin. I still can't see how to add myself to groups, but I'll learn the command line for that.

I just want to eliminate possibilities. We have a new Toshiba e-studio243 Photocopier Scanner Printer. Ubuntu correctly identifies it. I downloaded the Toshiba linux driver, a ppd file, and put it in /etc/cups/ppd/ but apart from a click when I say print, nothing happens!
may be a silly question:
have you restart your printer daemon. may be the configfile is read only once at startup.
cheers

---

### Post by Pedroski55 on 2012-12-20
Danke, ich hatte auch 

pedro@pedro-bedro:~$ sudo service cups restart eingegeben, doch bringt nichts!

---

