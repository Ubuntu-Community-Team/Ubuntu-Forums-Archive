---
title: "my system is going crazy"
date: 2014-04-24
forum: General Help
---

### Post by iamrandy on 2014-04-24
i have ubuntu 12.04.4 lts. and i just installed updates a little bit ago and instantly after it rebooted it started acting up. it froze the system a couple of times and then if i would pull up a folder it would be way off in the corner  and when i would go to move the box its leaving copies of itself behind itself as i move it. 


Can someone please help me

Thank you

---

### Post by iamrandy on 2014-04-25
i really just want to know then if this is a bug or not

---

### Post by iamrandy on 2014-04-25
and the internet is the only thing that will open and close reliably

---

### Post by jamesisin on 2014-04-25
Sounds like a video issue.  Do you know what was updated?

---

### Post by iamrandy on 2014-04-25
i'm sure i can find out but i don't know the commands.   Since you mention that. some additional driver updates came up when i first installed and they wouldn't install properly.

---

### Post by jamesisin on 2014-04-25
We can try running *sudo apt-get check* to see if there are any known missing dependencies.  After that I would also recommend running your updates afresh (*sudo apt-get update && sudo apt-get upgrade*).  Reboot.  If that does nothing that I would probably seek investigations concerning your video driver.

---

