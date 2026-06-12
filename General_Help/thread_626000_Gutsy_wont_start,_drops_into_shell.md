---
title: "Gutsy wont start, drops into shell"
date: 2007-11-28
forum: General Help
---

### Post by chriswinsatlife on 2007-11-28
I was having problems with a slow boot time, and made editions to menu.lst and another file to try and remedy it, but now gutsy wont boot. It sends me into shell, and then after a long time I get this message.

/dev/disk/by-uuid/9777873b-4c52-4e62-ae05-9e0e563e78f2 does not exist

I have no idea what to do, and I thoroughly searched the forums for this problem, but I couldn:t find anything that matched up with this specific error. I have no cd drive to reinstall, so preferable I can fix this without reinstallation or by getting files online.

Thanks in advance for the help, I really appreciate it.

---

### Post by Toet on 2007-11-28
Can you post your /etc/fstab?

---

### Post by chriswinsatlife on 2007-11-28
I should've posted it in the first place, but I actually fixed it. Turned out my menu.lst file was directing to the wrong partition. That just killed like 4 hours of my time. Thanks for the quick reply though.

---

