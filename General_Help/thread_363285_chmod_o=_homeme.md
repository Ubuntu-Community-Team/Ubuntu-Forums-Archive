---
title: "chmod o= /home/me"
date: 2007-02-16
forum: General Help
---

### Post by inunguak on 2007-02-16
I created other user accounts a long time ago, but a long time later did I realize that new users are by default able to list directory contents and read the contents of other users' home directories. Shouldn't they be restricted from doing so by default?

---

### Post by aysiu on 2007-02-16
No. By default, they can read other users' directories and files but cannot modify them.

If you *chmod* a particular file or directory, you can restrict that access.

---

### Post by WW on 2007-02-16
Depends what you mean by "should".  I agree that, even though the current default is to give the world read-access to your home directory, it *should* be no access.  I guess the current default is a holdover from the early, innocent and carefree days of unix.

A potential problem with using chmod o= /home/me arises if you use a web server and your home directory is in /home/me/public_html.  The web server probably won't be able to get to your files.  So on my accounts where I want to use public_html, I leave the o=rx permissions for my home directory and for public_html, but set everything else to have no world read permissions, and I also have umask=077. (Maybe denying group access by default is overkill, but it hasn't caused any problems so far.)

---

### Post by inunguak on 2007-02-17
Yes, by 'should', I meant it should be in order to be intuitive, for human beings.

I initially used the GUI to create accounts, and I just assumed that it would default to maximum security. The more advanced users can use the command line to change the permissions, but leaving it at the unix default wouldn't be that good for linux newbs.

---

