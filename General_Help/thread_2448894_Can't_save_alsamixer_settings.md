---
title: "Can't save alsamixer settings"
date: 2020-08-15
forum: General Help
---

### Post by raviolios2 on 2020-08-15
Hello, I'm a linux newb so please bear with me.  Whenever I restart my comp ( and occasionally at other times ), I can't hear anything through speakers or headphones.  To fix it have to go to the terminal -> alsamixer and turn up the speaker volume from 0 to whatever.  I can't seem to figure out how to keep those settings for the restart.  None of the research I've done on the topic has been successful either.  I was wondering if someone could help walk me through what I'd need to do to fix the issue.  Thanks!

---

### Post by cg-152 on 2020-08-16
The following should work:

- After entering alsamixer, press F6 to determine your card number

- Run the command "sudo alsactl store n", where n is your card number

- Run the command "sudo alsactl restore n" to restore your settings

- Add "sudo alsactl restore n" to your startup applications so it does it automatically every boot

---

