---
title: "Cold Boot hangs at &quot;starting samba daemons&quot;"
date: 2008-04-10
forum: General Help
---

### Post by swedishlf on 2008-04-10
I've had this issue for a while now.  Running gutsy amd64. 

 When I turn the computer on for the first time during the day, the system hangs at "Starting samba daemons" about 90% of the time.  I've let it sit for a solid hour here it's definitely frozen.  Odd thing is, if I hit the reset button, about 50% of the time, it will go straight through to the desktop, the other 50% of the time it reboots at hitting "Starting samba daemons."  In the event that it reboots it almost always goes straight to desktop.

This makes for unacceptably long boot times, and I can't imagine having to hit the reset button that often is too healthy for the comp.  Any ideas?  Let me know what further information you need.

---

### Post by swedishlf on 2008-04-15
I seem to have solved the problem by uncommenting the following lines in /etc/samba/smb.conf:

   winbind enum groups = yes
   winbind enum users = yes

If this is a bad idea for any reason, please let me know.

---

### Post by swedishlf on 2008-05-02
The problem was solved, but has resurfaced, no changes have been made to the afore mentioned file.  Weird.

---

