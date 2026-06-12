---
title: "reinstalling MySQL without losing databases"
date: 2007-06-01
forum: General Help
---

### Post by Pollywoggy on 2007-06-01
I am getting errors about the maintenance user account in MySQL being corrupted, and since I can't fix it, I think I should purge MySQL after backing up my Postfix database, then reinstalling.  Does anyone have any recommendations as to how to do this so that I don't just install a corrupted MySQL all over again?  I don't know how the debian-maint database got corrupted, I did not mess with it.

EDIT: Problem solved, reinstallation of MySQL was not necessary.

It appears that my database for Postfix caused the problem.  I changed the password in /etc/mysql/debian.cnf and then set the password for the debian-sys-maint user from within MySQL so that it matches the one in debian.cnf

I also fixed the corrupted mysql database and the error messages have disappeared.

---

