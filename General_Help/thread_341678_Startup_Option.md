---
title: "Startup Option?"
date: 2007-01-19
forum: General Help
---

### Post by Scooter7 on 2007-01-19
Hi, I was wondering if there's a way to set a program so it starts up when I log into Ubuntu.   I'm sure I saw an option for it somewhere... but I can't find it. :-k 

I'm using Ubuntu 6.10.

---

### Post by taurus on 2007-01-19
System -> Preferences -> Sessions -> Startup Programs -> Add.  Then, type in the name of the program you want to start and click OK.  Log out and back in again and see what happens.

---

### Post by Scooter7 on 2007-01-19
Hmm, that didn't seem to work.   I'm trying to get aMSN and Firestarter to start.   Thing is, I don't know where they're located in my filesystem.   I'm so new to Linux (only been using it for a week), so I'm used to my programs all being located in a Program Files folder... ](*,)

---

### Post by taurus on 2007-01-19
If you can start it from a terminal, then you can add it to your session since it's on your path.  Otherwise, you need to include the complete path to it.  So, see if amsn starts at all.

Applications -> Accessories -> Terminal
```
amsn
```

---

### Post by Scooter7 on 2007-01-19
Well, that worked, and I got it to start on startup.   It was just a matter of typing it in lowercase. :tongue:   Now, my only problem is that Firestarter won't start up on login because it says it needs administrator privileges... I can start it normally though.   How can I change this?

---

### Post by Johnsie on 2007-01-19
[http://ubuntuforums.org/archive/index.php/t-33615.html](http://ubuntuforums.org/archive/index.php/t-33615.html)
[http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)

---

### Post by Scooter7 on 2007-01-19
Hmm... I tried the more detailed second link, and it didn't work for me...

---

