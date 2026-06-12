---
title: "Problem with ttySO, /var/lock and permissions"
date: 2008-04-08
forum: General Help
---

### Post by 944_Driver on 2008-04-08
(Warning, I am quite new to Linux.)

I am trying to use digitemp to read a couple of temp sensors connected to the serial port (ttyS0) and it works fine if I run it with **sudo** in the terminal window. 

If I try to run it without **sudo** I only get:
*Error locking ttyS0. Do you have permission to write to /var/lock?*

I have tried to run **sudo chmod a+rw** on /dev/ttyS0 and /var/lock and on the file LCK..ttyS0 in /var/lock. I also deleted the LCK..ttyS0 file and tried again without any success until I run it with sudo again... Do I need to change any more permissions to be able to use the serial port as normal user since I don't think I should need to use sudo all the time or log in as root?

// Magnus

---

