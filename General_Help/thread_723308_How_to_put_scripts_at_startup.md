---
title: "How to put scripts at startup"
date: 2008-03-13
forum: General Help
---

### Post by dayanandasaraswati on 2008-03-13
Hi
   I've have a master and a slave hdd. In my slave i've installed linux. So my master partitions are detected very well but not mounted. So i everytime mount them manually. Instead i've written a shell script to mount them automatically. I want it to get executed at startup. So where do i put my script to get executed at startup

---

### Post by munkyeetr on 2008-03-13
Instead of using a script, you should add them to your /etc/fstab file, which will mount them for you.

See this thread for information: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by sisco311 on 2008-03-13
If you post your mount command, then we can help you with the fstab entry.

---

