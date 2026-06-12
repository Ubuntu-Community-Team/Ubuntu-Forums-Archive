---
title: "Problem with lampp permission"
date: 2013-12-03
forum: General Help
---

### Post by carlosl92 on 2013-12-03
Hi!

I've downloaded Lampp 1.8.3 and installed using their own script on a Xubunu 13.04 and it's installed correctly in "/opt/lampp" and works fine using root user.
My problem is the following: 
I want that a normal user can start and stop lampp but when I try typing "./lampp start" being normal user it says "Starting XAMPP for Linux 1.8.3-1..." and then "You need to be root to perform this action" and stops.

I tried changeing group and owner of all files and directories in "/opt/lampp" to user and I tried to edit sudoers file typing "usuari ALL=(ALL) !ALL NOPASSWD:/opt/lampp/* " ( usuari is the name of the user ) but it doesn't work.

Do yo know how can I solve it or have any idea to do this?

Thnak you!!!

---

