---
title: "[SOLVED] new home partition - I screwed up. (urgent)"
date: 2008-05-24
forum: General Help
---

### Post by jakupl on 2008-05-24
I tried making a seperate partition for /home but it did not work as I rebooted. then I logged into failsafe terminal session and changed fstab to the way it was before, put the home folder where it was and unmounted the home partition.
It still did not work.
Now when I look at it in the live session using the live cd. I see that the home backup has the correct users. my own folder has user 1000 listed as owner and the other folder has 1002 listed as owner. When I try to move it into the correct place (/home) the owners change to root. Therefore I cannot login.

Any help would be greatly appreciated as I really need to use the computer at 16:00 gmt.
Thank you.

---

### Post by cdtech on 2008-05-24
You can change the owner with:
sudo chown -R "theowner" /home

---

### Post by jakupl on 2008-05-24
wow! that worked.

I really have to learn these commands. What a stupid problem.

well thankyou very much.

---

### Post by cdtech on 2008-05-24
Yu welcome.

Good luck.......

---

### Post by hyperair on 2008-05-24
If you ever need to change it in a LiveCD system, use the numbers instead, because the user on the LiveCD system may differ from the user on your system.

---

