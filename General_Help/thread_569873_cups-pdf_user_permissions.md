---
title: "cups-pdf user permissions"
date: 2007-10-07
forum: General Help
---

### Post by scotthompson on 2007-10-07
I have set up cups-pdf on ubuntu server 6.06 to output my "printed" files to a directory on my web server.  Everything works great except the user file permissions.  Only the 'owner' who created the file can read/write; 'users' and 'others' file permissions are set to forbidden.  How can I change this?

---

### Post by mexlinux on 2008-07-04
(this is a reminder for my self for future updates)

You have to modify the "UserUMask" Variable to something like 0033
Warning on confidential information!

To change the outpute path
Modify the "Out" variable in /etc/cups/cups-pdf.conf
And set the permissions in /etc/apparmomr.d/usr.sbin.cupsd
for the corresponding new folder
and restart apparmor

---

