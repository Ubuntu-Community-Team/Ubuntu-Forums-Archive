---
title: "Very slow boot time"
date: 2007-06-10
forum: General Help
---

### Post by mack1082 on 2007-06-10
Hi everyone, I'm a long time Gentoo user that just switched over to ubuntu.  I really like the usability and hardware compatibility, the only problem is the boot time.  I installed bootchart and attached the generated png file for review.  If anyone can help me out I'd really appreciate it.  

It looks like to me like modprobe is hanging everything up, but to tell you the truth I'm not 100% sure of how to read the image.

---

### Post by tpg on 2007-06-10
I'd agree with you, modprobe seems to be the culprit. It strikes me that the computer doesn't seem to be "doing anything" for over a minute, while modprobe loads.

Maybe have a look inside /var/log/messages and /var/log/boot to see if it gives you any clues. If that doesn't help, trying passing the verbose option to the kernel at boot time, and see if it gives any extra information.

---

