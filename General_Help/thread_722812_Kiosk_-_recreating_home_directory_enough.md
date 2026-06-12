---
title: "Kiosk - recreating home directory enough?"
date: 2008-03-12
forum: General Help
---

### Post by rhy7s on 2008-03-12
Is recreating the user home directory for a guest account an effective method for creating a kiosk as per this [link]("http://www.linuxactionshow.com/forum/comments.php?DiscussionID=1367")? For step 1:
"1. limit the directories the users have access to (probably just to /home/username)" - can anyone expand on what directories would need to be changed to achieve that? Thanks.

---

### Post by Oldsoldier2003 on 2008-03-12
> **rhy7s said:**
> Is recreating the user home directory for a guest account an effective method for creating a kiosk as per this [link]("http://www.linuxactionshow.com/forum/comments.php?DiscussionID=1367")? For step 1:
"1. limit the directories the users have access to (probably just to /home/username)" - can anyone expand on what directories would need to be changed to achieve that? Thanks.

try using KDE in kiosk mode...  

[http://developer.kde.org/documentation/tutorials/kiosk/index.html](http://developer.kde.org/documentation/tutorials/kiosk/index.html)

---

### Post by rhy7s on 2008-03-12
I'd like something a little more WM agnostic than KDE kiosk, but it's probably the most integrated solution out there for systems meeting the higher hardware requirements of KDE I'd imagine though.

---

### Post by pointone on 2008-03-13
You can disable the write+execute bits on everything besides the user's home directory for the "other" user permission. This would prevent the user from stepping outside their home directory, in theory, and even if not completely, they wouldn't be able to change anything.

I was never able to reliably accomplish this for an Internet kiosk I developed (only runs a web browser), aside from preventing any file browser popups (i.e., disabling open / save, no application laucher available, etc.) Opera's open / save dialog, for example, still allowed browsing around the filesystem. (They couldn't write/change anything, but I still wanted to prevent all access.)

I'm curious about this as well, if you find a better solution!

---

