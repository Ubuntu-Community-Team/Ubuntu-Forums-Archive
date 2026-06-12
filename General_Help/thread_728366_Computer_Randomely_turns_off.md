---
title: "Computer Randomely turns off"
date: 2008-03-18
forum: General Help
---

### Post by Mostlyharmless42 on 2008-03-18
So, originally i thought this was an OS problem, but it now appears that it might be a hard ware problem.  The problem is that my computer will turn itself off randomly.  It started about 2 months ago and has been getting more and more frequent.  From once a week to once a day to now every hourish.  Originally it was only while the computer was booted into linux and i wasn't using it, but starting yesterday it started to do it while i was in the middle of something.  Yesterday it turned off while i was trying to post this and when i went to turn it on it would stay on for about a second and turn off.  I tried a few more times and the uptime would vary from not even enough time to boot to about 10 mins.  I got into bios and everything looked fine and my temperatures were in a normal range, so it doesn't seem to be a cooling issue.  When i came in today it turned on fine and has been running for about 15 mins now.

Does anyone know what the problem could be???

---

### Post by Athelstan101 on 2008-03-18
You could try looking in the system log to see if there's any useful messages:
```
$ sudo tail /var/log/messages
```

---

