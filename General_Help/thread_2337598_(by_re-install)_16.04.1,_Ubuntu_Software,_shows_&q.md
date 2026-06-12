---
title: "(by re-install) 16.04.1, Ubuntu Software, shows &quot;no application data found&quot;"
date: 2016-09-20
forum: General Help
---

### Post by Kris_M on 2016-09-20
is there a fix for that?
Thanks.

---

### Post by CantankRus on 2016-09-20
Try this.
In Ubuntu Software go to the updates tab and hit the refresh button at top left.
Install any updates then close and reopen Ubuntu Software.

---

### Post by Kris_M on 2016-09-20
Thanks. I did, but stilll nothing.

I just tried about a dozen different things and none of them worked.

---

### Post by CantankRus on 2016-09-20
Try fix from askubuntu.... [http://askubuntu.com/questions/760278/the-new-software-center-in-ubuntu-16-04-shows-no-application-data-found](http://askubuntu.com/questions/760278/the-new-software-center-in-ubuntu-16-04-shows-no-application-data-found)

---

### Post by Bucky Ball on 2016-09-20
Best fix for this is to install Synaptic Package Manager until the issues are sorted out with Ubuntu Software. They are known and ongoing.

```
sudo apt-get install synaptic
```

---

### Post by JamButty on 2016-09-20
ditto. Went to "Language Support" under settings, got something like "no data found", accepted update suggestion. After reboot Software was "sort of" normal.  Another bug is that after a package is installed, the program, in previous incarnations, changed the button from "install" to "remove", indicating the installation was complete. Now it remains on "install" even after completion, even after using the installed program. Multiple restarts of the installer program does not change this. Presumably, it wakes up on reboot of system.
The Xenial Squirrel is very squirrely...had to wipe and reload whole system just before this due to blank screen after login.....

---

### Post by Kris_M on 2016-09-20
Thanks all. No joy.  I've got some CZ parts from the 15th, 17th, and 19th and I will try them later today.  Hopefully I can get to before it happened.

---

### Post by Kris_M on 2016-09-20
I gave up and reinstalled 16.04.1  So far I have FF, TBird, playonlinux, 2 games installed with wine, psensor, and all seems fine.  I am CZing often so I don't lose so much next time.

---

