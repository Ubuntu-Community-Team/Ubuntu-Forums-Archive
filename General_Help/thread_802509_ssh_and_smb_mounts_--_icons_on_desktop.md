---
title: "ssh and smb mounts -- icons on desktop"
date: 2008-05-21
forum: General Help
---

### Post by JasonKretzer on 2008-05-21
One of the things I liked about 7.10 was that when I mounted internal drives and remote smb/ssh locations icons were created on the desktop.  Then they automagically reappeared when I rebooted.  Why in the world would they(they being a general whoever is responsible) remove this automounting magic?  

Anyway, trying to reinvent the wheel here to get the same behavior in 8.04.  I added the automounting for the internal drive to the fstab and that works fine.  However, I cannot get the automounting of smb/ssh locations to show icons on the desktop.  I created them using Places-> Connect to Server...  and even added them as a bookmark(which is not the same).  

An example of the behavior I expected.  In 7.10, I created a Windows share using the same process as above.  I entered in the username and domain and when I tried to access it would ask for my domain password.  It would "remember" all my other information besides password(cause I told it not to).  In 8.04, it remembers nothing(using the bookmark because I have no desktop icon).  The ssh bookmark does act as I would expect.

Basically, how do I re-enable the behavior for these(ssh/smb mounts desktop icons) as was in 7.10?

---

### Post by JasonKretzer on 2008-05-23
**Bump** anything? anything at all?

---

### Post by lofftjm on 2008-07-15
Run gconf-editor and navigate to /apps/nautilus/desktop/ and check/uncheck items that you do / do not wish to display.

---

