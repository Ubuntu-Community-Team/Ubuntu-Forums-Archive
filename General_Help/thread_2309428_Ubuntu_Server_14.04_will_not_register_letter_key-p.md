---
title: "Ubuntu Server 14.04 will not register letter key-press"
date: 2016-01-10
forum: General Help
---

### Post by Blakstar26 on 2016-01-10
As the title describes, my Ubuntu Server install will not register my key-press of lowercase "a". Uppercase "A" is fine, as well as all other letters. It will print the letter "a" to screen but will not accept a key-press or a copy/paste that includes "a". 

This began after a power outage a few days back, after restart. Never experienced this before, so I'm stumped.

Any suggestions??

---

### Post by Blakstar26 on 2016-01-10
Ok, I kind-of sort-of solved it by renaming my **.inputrc** file per the recommendation [HERE]("https://askubuntu.com/questions/411925/unable-to-use-type-letter-d-within-terminal-on-ubuntu-13-10"). 
Knowing that file was causing the problem, I commented out each line until i found the problem and it turned out to be a specific line that read "**show-all-if-ambiguous on**". I'm not sure why this caused the problem I'm having but I'll take it. 

Leaving this here for someone else that may have this problem.

---

