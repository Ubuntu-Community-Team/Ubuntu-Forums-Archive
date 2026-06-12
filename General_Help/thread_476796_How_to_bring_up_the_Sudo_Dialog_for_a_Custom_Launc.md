---
title: "How to bring up the Sudo Dialog for a Custom Launcher?"
date: 2007-06-17
forum: General Help
---

### Post by sbjaved on 2007-06-17
I downloaded DRIConf from the repos. I wanted to place a launcher on the desktop, so i created one but since DRIConf requires 'sudo' priviliges...it gives errors. 

How can i bring up the sudo authentication dialog for my launcher?

Thanks.

---

### Post by Raavea on 2007-06-17
Have you tried setting the launcher to execute the command **sudo driconf**  ? As far as I recall, that used to make my launchers bring up a admin-password request box thingy. (I don't have launchers any more, so can't check for you.)

---

### Post by s.deleeuw on 2007-06-17
Edit the launcher to make it run: 'gksu driconf'.

---

### Post by sbjaved on 2007-06-18
> **s.deleeuw said:**
> Edit the launcher to make it run: 'gksu driconf'.
Thankyou. That did the trick! Although I used 'gksudo' instead of 'gksu'...its the same isn't it?

---

