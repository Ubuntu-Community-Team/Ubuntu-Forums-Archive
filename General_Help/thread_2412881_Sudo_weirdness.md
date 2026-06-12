---
title: "Sudo weirdness"
date: 2019-02-18
forum: General Help
---

### Post by nselby on 2019-02-18
Suddenly I have been kicked out from sudo in terminal. My user is an administrative user according to the Settings -> User dialogues. 

I can still install (using my password as administrative user in the GUI), but if I pop open a terminal and do sudo foo and try to authenticate it fails. I can also not su - . 

I have dropped into the recovery boot mode, mounted / as rw and done adduser [user] sudo and been told that the user is already in the sudo group. 

I did note that the admin group had been deleted. I recreated it, added my user to admin group. Rebooted. Still cannot sudo anything in terminal. 

This is frustrating. Any ideas? 

Thanks in advance

---

### Post by deadflowr on 2019-02-18
Duplicate thread
[https://ubuntuforums.org/showthread.php?t=2412883]("https://ubuntuforums.org/showthread.php?t=2412883")

Thread Closed

---

