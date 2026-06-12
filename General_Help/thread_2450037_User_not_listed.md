---
title: "User not listed"
date: 2020-09-06
forum: General Help
---

### Post by zkab on 2020-09-06
I have Ubuntu 20.04 LTS.
When I reboot and get the first screen it shows under the user image & name 'not listed'
How do I get the user listed?

---

### Post by yapidumoac on 2020-09-07
[User Not Listed In GDM Login Screen]("https://ubuntuforums.org/showthread.php?t=1410702")

---

### Post by zkab on 2020-09-07
I followed the link but  this is what I got ...

$ sudo usermod -u 1001 forsete
usermod: user forsete is currently used by process 1818

---

### Post by grahammechanical on 2020-09-07
Excuse me If I am not understanding the problem clearly. Are you able to log in? How many users are there on this machine?

If we are the only user then at the login screen we simply type in a password and press enter. If we click "User not listed?" we get another screen where we can type in a user name. Then when we press enter we get a password panel and if we have the correct user name and password we get a desktop.

If we want to add a user we do that through System Settings>Users. We will need to unlock the utility before we can add or remove a user. And we must be the user whose password gives them administrator authority.

I am the only user on my machine so I have no information as to what the login screen would show if there was more than one user on the system. Perhaps a drop down list of users? I do not know.

Regards

---

### Post by zkab on 2020-09-08
I am the only user (forsete) at the computer.
If I hit return then I get the password screen where I login successfully.
There is no big issue with 'not listed' ... I was just curious why the system tells me that for the only user ... listed where ???
If there is no way to get rid of not-listed on the first after-boot-screen then I consider the problem solved ... without understanding why system behaves like this.

---

