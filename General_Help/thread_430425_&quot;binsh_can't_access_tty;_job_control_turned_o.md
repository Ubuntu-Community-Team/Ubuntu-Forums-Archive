---
title: "&quot;/bin/sh: can't access tty; job control turned off&quot; problem after installing new HD"
date: 2007-05-02
forum: General Help
---

### Post by Lobosque on 2007-05-02
Hello Guys. I need help so bad.
The matter is:
I have a 80GB IDE HD with ubuntu (ext3 and swap). Today I installed a 160GB HD and i put Windows in it.
Now when i try to boot from the HD with Ubuntu in it, i get this error (the bar progress loads about 1/10 and then i get the console with message):
```
/bin/sh: can't access tty; job control turned off
```
I have read a LOT of topics about this problem, but no one helps me at all, since 95% of the people get this problem with live CD, and its not my case.
Anyone know what I should do? Thanks.

---

### Post by sharke on 2007-05-02
Can you boot to widows.
How did you install windows did you just install new drive and then installed windows before you booted ubuntu.
regards
Sharke

---

### Post by Lobosque on 2007-05-03
Yes, i can boot windows.
Yes, i installed the windows in the brand new HD before boot Ubuntu

---

### Post by sharke on 2007-05-03
Okay the problem is caused by windows always tries to take boot controll after install . Open her up disconnect windows drive snd see if you  can boot ubuntu ifso post a copy of your /boot/grun menu.list
Regards
Sharke

---

### Post by Lobosque on 2007-05-03
Even if I remove the windows HD Ubuntu do not boot up.
What should I do now?

---

### Post by markoloka on 2007-05-04
To me it happens when i try to install. So it's not just live cd problem. Either windows doesn't have anything to do w/ this problem.

---

### Post by sharke on 2007-05-04
No If buts Or Maybe your problem is caused by installing windows after linux to fix go here [http://ubuntuforums.org/showthread.php?t=24113&highlight=howto+restore+grub+with+live+cd](http://ubuntuforums.org/showthread.php?t=24113&highlight=howto+restore+grub+with+live+cd)
Regards
Sharke

---

