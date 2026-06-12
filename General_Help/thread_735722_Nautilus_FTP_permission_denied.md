---
title: "Nautilus FTP: permission denied"
date: 2008-03-25
forum: General Help
---

### Post by andrewbootlegger on 2008-03-25
Tried connecting to an FTP server I use with a team of software developers.  Upon connecting, I got: Nautilus cannot display "ftp://user@site.com:21/home/user".  I am denied access to the homes directory, but can use my directory.  According to a capture from wireshark, Nautilus tries to CWD through each directory in the path.  For example:    

  cd /home
  cd user

This generates an error: 

550  /home: Permission denied.

Nautilus then disconnects.

I tried leaving the directory option blank, but Nautilus immediately CWDs to the root directory (ordinarily, I'm dropped in my home dir).  Is there a way to change Nautilus' behavior? :confused:

---

### Post by dcstar on 2008-03-26
> **andrewbootlegger said:**
> Tried connecting to an FTP server I use with a team of software developers.  Upon connecting, I got: Nautilus cannot display "ftp://user@site.com:21/home/user".  I am denied access to the homes directory, but can use my directory.  According to a capture from wireshark, Nautilus tries to CWD through each directory in the path.  For example:    

  cd /home
  cd user

This generates an error: 

550  /home: Permission denied.

Nautilus then disconnects.

I tried leaving the directory option blank, but Nautilus immediately CWDs to the root directory (ordinarily, I'm dropped in my home dir).  Is there a way to change Nautilus' behavior? :confused:

Doubtful, lodge a bug for it.

---

