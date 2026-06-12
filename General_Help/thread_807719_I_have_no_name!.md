---
title: "I have no name!"
date: 2008-05-26
forum: General Help
---

### Post by ajeetraina on 2008-05-26
Hello Guys,

I have a Ubuntu Fiesty Linux which displays the following at the time I supply the following commands:


Code:
vjs@micex:~$ sudo /etc/init.d/apache2 restart
sudo: no passwd entry for root!
vjs@micex:~$I tried logging through runlevel 1 but all it ends saying:


Code:
chown: root-tty:invalid user
su-login cannot open passwd database 
Segmented Fault
init:rcS-sulogin main process(3801) terminated with status 139.
-
-
-Its just displaying cursor and nothing ahead.


I followed [http://www.cyberciti.biz/tips/recove...word-file.html](http://www.cyberciti.biz/tips/recove...word-file.html)
and ran :

1. Rebooted
2. Edit Recovery Mode : with init=/bin/bash
3. mount -rw -o remount /
4. Edited /etc/passwd file(Surprisingly nano editor was working but vi dint)
5. Moved passwd- to passwd and moved shadow- to shadow.
6. Forcibly rebooted.

Now it seems to work. But it displays:

I have no name!@micex:~$


Why it is displaying so??

---

### Post by Rinzwind on 2008-05-26
Answer is in this topic from 2006 that you kicked 15 minutes ago:
[http://ubuntuforums.org/showthread.php?t=153721](http://ubuntuforums.org/showthread.php?t=153721)

Why do you need 2 topics asking the same thing? Hmm?

In case you missed it:
[http://ubuntuforums.org/showpost.php?p=883233&postcount=3](http://ubuntuforums.org/showpost.php?p=883233&postcount=3)

"When that happened to me, it was because I had set /etc/passwd to be read-inaccessible to non-root users, thinking it would be more secure."

You changed the file parameters at point 4 or 5.

---

