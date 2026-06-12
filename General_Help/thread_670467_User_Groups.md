---
title: "User Groups"
date: 2008-01-17
forum: General Help
---

### Post by DanGahan on 2008-01-17
Hi, hopefully someone can help me with a problem I have created.

I have recently installed a fresh copy of ubuntu 7.10 on my machine, and since the install I have not set a password for the root account.

Here's where I created my problem, I wanted to add my only user to a new group I had created, but in doing so I made the error of removing him from his original groups, leaving me with no sudo access.

As I have no sudo access and the root account has not had a password set, is there a way from me to add my user back to the default groups or will it require a fresh install.

Many Thanks 

Dan Gahan

---

### Post by sisco311 on 2008-01-17
reboot in recovery mode(select the second option from grub menu)

add your user to administrator group:
```
usermod -a -G admin **username**
```reboot in normal mode

next time use the
```
sudo usermod -a -G group_name1(,group_name2,...) username
```command to add user the supplemental group(s) or use the gui(Users and Groups)

---

### Post by DanGahan on 2008-01-17
Cheers, always good to learn from our mistakes.

---

