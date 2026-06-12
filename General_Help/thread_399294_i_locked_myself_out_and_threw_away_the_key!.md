---
title: "i locked myself out and threw away the key!"
date: 2007-04-02
forum: General Help
---

### Post by aata on 2007-04-02
okay. here is the deal.
recently, i've been being an idiot. i got the new release of edubuntu, edgy, and installed it on my fairly new pc. anyway, i soon noticed that 1) applications that run in the background (i.e gnome-update-manager when you close them, do not show up in the system tray, 2) my openoffice.org refused to work - giving an internal java error, and 3) firefox suddenly decided to make my start page "www.%u.com". 
all these issues were non-existent in any of the other 2 user accounts on the system (with me being the administrator). i got thinking (apparently i shouldn't have been) and decided to make a new test user, make sure that all my applications work on that, leave my old account behind, and make the test account my own. 
in my infinite wisdom, i decided to modify the old root account - i.e deauthorize it, and authorize the new tester account to be an administrator.
therein lay my undoing. i restarted the system and found that the accounts had been renamed appropriately, BUT, none of them were left with system priveliges!
what in the world can i do?!?
thanks in advance
cookieman

---

### Post by g8m on 2007-04-02
Is it possible to boot with the live-install cd, mount your existing install
and sudo gedit your /etc/sudoers file, add a user?

---

### Post by teaker1s on 2007-04-02
look here I've helped with similar issue, you should also edit sudoers file with 
```
visudo
```
[http://www.ubuntuforums.org/showthread.php?t=398560]("http://www.ubuntuforums.org/showthread.php?t=398560")

---

### Post by aata on 2007-04-02
these are very good suggestions, and quite possibly would work, if any of the passwords i have worked!
what i mean to say is that if i try to sudo something, it asks me for a passwor, right? then, no matter what password i enter, it denies me access!
thats the problem!
cookieman

---

### Post by teaker1s on 2007-04-02
your need to use live cd if recovery kernel login borked as well

---

### Post by aata on 2007-04-02
ok... that might work.
but i'm afraid to say that i'm not THAT advanced a user... could you guide me throught the steps?
cookieman

---

### Post by teaker1s on 2007-04-02
while I've yet to suffer a truely borked system and need live cd,  my best advice is the link below
[https://wiki.ubuntu.com/LivecdRecovery]("https://wiki.ubuntu.com/LivecdRecovery")

:popcorn:

---

