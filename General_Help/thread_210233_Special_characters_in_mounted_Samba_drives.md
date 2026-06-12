---
title: "Special characters in mounted Samba drives"
date: 2006-07-06
forum: General Help
---

### Post by mattG on 2006-07-06
I am mounting a Samba drive using the following entry in /etc/fstab:

//server/user /samba/home smbfs defaults,uid=1000,gid=1000,credentials=/home/user/.smbpasswd,umask=777 0 0

In general this works fine. However, I get into problems with directories and files that contain special characters (e.g. the German "äöü"). Neither the terminal nor Nautilus are able to display these characters and many applications fail opening such files or directories.

I found the advice to add "iocharset=iso8859-1,codepage=cp850" - However, this didn't solve the problem. (As far as I am informed, the Samba server I am connecting to is configured to use iso8859-1).

Does anyone have any ideas? Many thanks in advance!

---

### Post by ShiftyPowers on 2006-07-08
yeah, I have the exact same problem.  A lot of my music which is from Brazil has special characters and I can't get them to look right.  I have the PT locale installed but it still doesn't work right.  Also sometimes, when I click on the file that has a special character the files disappears in Nautilus.

---

