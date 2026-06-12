---
title: "[SOLVED] dpkg error, cant run add/remove programs anymore...please send in the nation"
date: 2007-08-27
forum: General Help
---

### Post by djhvt on 2007-08-27
I was trying to run:
sudo apt-get install ubuntu-restricted-extras

When it got to the Sun drivers portion the screen changed (a blue DOS like screen) and asked me to confirm a user agreement, however the terminal would not allow me to confirm via the enter key, or any other method...so i closed the screen and gave up on Sun.

That said when i came back later and tried to use the add/remove program app it wouldnt work and gave me the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I reported it to launchpad because it said to report....any idea how to fix this though?

thanks so much for all you do everyone!

---

### Post by sumguy231 on 2007-08-27
You need to go to a terminal and run 'sudo dpkg --configure -a'. That will fix it.

---

### Post by aJayRoo on 2007-08-27
Also if you want to install that package again, you need to press the tab key when you get to the license agreement screen to highlight the OK/I Agree button (or whatever else it may be called!) and then you will be able to press enter to accept.

---

### Post by djhvt on 2007-08-27
Thank you both so much! im up and running with gas now.

---

