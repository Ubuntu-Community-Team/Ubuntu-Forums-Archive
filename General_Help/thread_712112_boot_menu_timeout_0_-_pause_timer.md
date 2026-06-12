---
title: "boot menu timeout 0 - pause timer?"
date: 2008-03-01
forum: General Help
---

### Post by jagi gyamcho on 2008-03-01
I just installed Ubuntu 7.10, and after countless hours of trail and error I was finally able to have XP boot by default. 

However when I got XP to boot by default I also changed the  boot menu timeout to 0 so that it would automatically boot to it. But I didn't realize that by setting the "timeout" to 0 I wouldn't have enough time to access grub and boot to Ubuntu, and now I'm locked out of Ubuntu (the irony)

Is there a way I can pause the "timeout" during boot so I can boot to Ubuntu?

Any Help would be appreciated

---

### Post by taurus on 2008-03-01
1.  Boot with the LiveCD, mount your partition where / (or /boot if you have a separate /boot partition), and edit /boot/grub/menu.lst.

2.  Install fs-driver in XP and access your Linux partition and edit /boot/grub/menu.lst.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

p.s.  I would change the timeout to 3 seconds to give you a little time to react.

---

### Post by jagi gyamcho on 2008-03-01
Thanks I'll try that out!

---

### Post by jagi gyamcho on 2008-03-01
Well I tried the second option with installing fs friver to xp, but what other program do I need to edit the menu.lst file?

---

### Post by taurus on 2008-03-01
notepad?

---

### Post by jagi gyamcho on 2008-03-01
Wow, stupid me:confused:

Fixed the problem

Thanks a lot taurus

---

