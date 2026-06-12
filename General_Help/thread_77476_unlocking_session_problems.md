---
title: "unlocking session problems"
date: 2005-10-16
forum: General Help
---

### Post by sauyeeluo on 2005-10-16
i've been having a problem unlocking a session. i enter the correct user password but unlocking always fails. i have tried both my regular and root account and unlocking fails for both accounts. 

any ideas whats going wrong?


thanks

---

### Post by savastux on 2005-10-31
[quote=sauyeeluo]i've been having a problem unlocking a session. i enter the correct user password but unlocking always fails. i have tried both my regular and root account and unlocking fails for both accounts. 

any ideas whats going wrong?


thanks[/quote] 

Same thing here! :cry:

savastux

---

### Post by dseg on 2005-11-24
[QUOTE=sauyeeluo]i've been having a problem unlocking a session. i enter the correct user password but unlocking always fails. i have tried both my regular and root account and unlocking fails for both accounts. 

any ideas whats going wrong?


thanks[/QUOTE]


Bump. 

I'm getting the same thing. I can start a new session with the same password, but not unlock the original.

---

### Post by wanger123 on 2005-11-24
Yep, same for me!:confused: 
wayne

---

### Post by dseg on 2005-11-25
[QUOTE=dseg]Bump. 

I'm getting the same thing. I can start a new session with the same password, but not unlock the original.[/QUOTE]


Opened bug in Bugzilla.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=20071](https://bugzilla.ubuntu.com/show_bug.cgi?id=20071)

More info: this worked without problems with original 5.10 install. Stopped working after update/upgrade.

Another thread to track:

[http://www.kde-forum.org/post/55009/lastpost.html#post55009](http://www.kde-forum.org/post/55009/lastpost.html#post55009)

---

### Post by dseg on 2005-11-25
[QUOTE=dseg]Opened bug in Bugzilla.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=20071](https://bugzilla.ubuntu.com/show_bug.cgi?id=20071)

More info: this worked without problems with original 5.10 install. Stopped working after update/upgrade.

Another thread to track:

[http://www.kde-forum.org/post/55009/lastpost.html#post55009](http://www.kde-forum.org/post/55009/lastpost.html#post55009)[/QUOTE]


Update:


"Changing the suid bit on the file /usr/bin/kcheckpass seems to fix the problem:

chmod 4755 /usr/bin/kcheckpass

"

from: [http://dot.kde.org/1029735436/1029783258/1029831850/](http://dot.kde.org/1029735436/1029783258/1029831850/)

Make sure you run "chmod" as root (or use sudo).

---

### Post by santo on 2005-12-07
Very nice.
I experienced the same whenever my laptop came out of suspend.
changing the suid bit of that file solved the problem indeed.

Thanks

---

