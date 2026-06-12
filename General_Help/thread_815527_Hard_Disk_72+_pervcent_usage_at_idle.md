---
title: "Hard Disk 72+ pervcent usage at idle"
date: 2008-06-01
forum: General Help
---

### Post by gearshifter on 2008-06-01
Just installed ubuntu a few hours (reinstall).

For some reason, watching the hard drive status, it is constantly at 70% or more in use and not stopping.  I cannot figure out what the heck is using my drive.

---

### Post by Lord Xeb on 2008-06-01
Hold on, what do you mean your drive? do you mean your Processor? If it is at 70%, try going into System Monitor and look for offender (the one using the most CPU usage). If your HDD is at 70%, then your HDD's space is 70% used. How big is your drive? When you post, you need to be more explainitory.

---

### Post by gearshifter on 2008-06-01
Just want to give an update:

I was talking about my Hard Disk constantly writing.

The underlying issue was my mythtv-backend.  For some reason the password was not set correctly in the mysql.txt in /etc/mythtv and not only would the backend not startup, but it was causing my harddrive to run constantly.

Once I fixed that, I hit 2 birds with one stone.  mythbackend would start at startup without having to add it to sessions, and the hd isn't roaring.

---

