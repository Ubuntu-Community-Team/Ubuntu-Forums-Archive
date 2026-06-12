---
title: "how to view boot messages"
date: 2007-09-05
forum: General Help
---

### Post by emanresu on 2007-09-05
how do i view the checklist of messages that the computer goes through when it boots? i saw it say something about "failed" for something related to NTFS, but it went by so fast, i couldn't tell what it was saying.

---

### Post by sumguy231 on 2007-09-05
Try looking at /var/log/boot.

---

### Post by emanresu on 2007-09-06
i did. there was no log there.

---

### Post by notwen on 2007-09-06
open up a terminal and type 'dmesg' this should printout a log of all services started at bootup, including the ones that failed to start. =] Hope this helps.

---

### Post by emanresu on 2007-09-06
thank you, that kind of worked. 

i would like it though if there was a way to read, as a made-up example:

AVAPI-HD                                                                [ok]
ntfs                                                                          [ok]
app-armor                                                                [failed]
udev                                                                        [ok]

the list that looks like that when the computer boots. i guess you don't normally see it because of the "Ubuntu" with the progress bar that is on the screen until the login screen.

---

### Post by skroops on 2007-12-18
this thread provides instructions to log your boot messages:

[ubuntuforums.org/showthread.php?t=49925]("ubuntuforums.org/showthread.php?t=49925")

---

