---
title: "denyhosts not working?"
date: 2008-03-13
forum: General Help
---

### Post by android6011 on 2008-03-13
I installed denyhosts using apt-get and it is running, then i tried some on purpose failed logins from another network as root and it never blocked me, i could keep trying without problems. what is wrong?

can a mod move this to server platforms? sorry

---

### Post by TurboRush on 2008-03-13
Have you adjusted the configuration for the number of times to allow a failure before being banned? Take a look at your denyhosts.cfg and check out this line...

```
DENY_THRESHOLD_INVALID = 5
```

Where 5 is the number of attempts you get.

Here is a good how to: [http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

---

### Post by android6011 on 2008-03-13
does it immediately block it after that many failed attempts? that is what i have set. or does it just block bad ips every so often? if that is the case how do i set how often it blocks the bad hosts? thanks

---

### Post by android6011 on 2008-03-13
bump

---

### Post by android6011 on 2008-03-14
it works i didnt realize that one putty session counts as 1 failed login attempt, so if that number is 5, then you can try to login in 35 times before it locks you out since each putty session lets you try to enter the password 7 times before you get a server disconnect message

---

