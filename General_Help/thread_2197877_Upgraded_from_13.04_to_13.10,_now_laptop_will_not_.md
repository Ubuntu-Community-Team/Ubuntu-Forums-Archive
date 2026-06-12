---
title: "Upgraded from 13.04 to 13.10, now laptop will not resume after lid closed"
date: 2014-01-05
forum: General Help
---

### Post by liquidcross on 2014-01-05
I'm using an IBM/Lenovo Thinkpad R60. The upgrade went smoothly, but now when I close the lid, the computer will suspend just fine...but will not resume when opened. It just goes to a black screen with a mouse cursor, and pressing the power button shuts down the computer (usually have to hold to do so, but the Ubuntu logo appears). Any idea? I know this is a common problem, but I have not yet found a solution.

---

### Post by liquidcross on 2014-12-15
Need to bump this post. After a clean install/downgrade to 12.04 LTS in the spring, I finally upgraded to 14.04 LTS...and now I've got the same lid problem again. Has anyone else run into this problem, and been able to fix it?

---

### Post by mörgæs on 2014-12-15
It seems like there is a pattern: A clean install works, an upgrade fails.
Leads me to ask if you have tried a clean install of 14.04.1?

---

### Post by liquidcross on 2014-12-15
Forgot to mention: I had clean-installed 13.x a while back, too. Same problem. I think it's something to do with newer incarnations of the OS.

---

### Post by Hughze on 2015-08-16
I've been finding with lenovo thinkpads that a failure to resume after suspend seems to be a graphics driver problem. Check your graphics card.  If it's NVIDIA, you need to install a NVIDIA propriety driver. With 14.04 LTS, you do that by going to the system settings, open the software updates on the bottom and then the additional drivers tab. If it isn't that way in 13.10 then you should be able to find the means in the software center.....

---

### Post by QIII on 2015-08-16
Rest in peace, dear thread.

---

