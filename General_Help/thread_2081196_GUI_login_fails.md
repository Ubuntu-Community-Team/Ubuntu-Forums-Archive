---
title: "GUI login fails"
date: 2012-11-06
forum: General Help
---

### Post by iamroddo on 2012-11-06
I'm running Ubuntu 12.10 on a AMD-64 system that has been upgraded a few times starting in 10.10. For some reason, probably due to some meddling by me, one user (my regular one) can no-longer log into a graphical session. I'm authenticated then kicked back to the logon window. Admin and the other user on the system can login graphically. I can login via a console. If I delete the user (and all user home directory files) and recreate it with the same username the issue remains. If I create a user with a different username logon works fine, until I rename the user (done via Webmin) to that of the affected username, at which point GUI logon stops working. I guess there's something left over in a configuration file for that username that doesn't get cleaned up but I don't know what. Can anyone suggest what I should do to resolve this?

---

### Post by thnewguy on 2012-11-06
When you deleted your home directory files, did you delete the entire folder and all of the configuration files inside? Also, when you create a ne wuser account try making use the new UID isn't the same as the old one. For example, if you had user ID 1000 before, make sure you use something different, like 1001.

To me it sounds like a left over configuration file in your home directory. I've seen something like this before and deleting all of the configuration files for my desktop environment fixed the problem.

---

### Post by iamroddo on 2012-11-06
When I deleted the user I also deleted the entire home directory. Using the same username but different UID is the same as with the same UID. There's something about the username that causes the issue.

---

### Post by 2F4U on 2012-11-06
Did you look into .xsession-errors in the home folder of the user with the problems?

---

### Post by iamroddo on 2012-11-06
No file by the name of .xsession-errors is created.

---

