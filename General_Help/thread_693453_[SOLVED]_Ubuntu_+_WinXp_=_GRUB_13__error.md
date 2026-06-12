---
title: "[SOLVED] Ubuntu + WinXp = GRUB 13  error"
date: 2008-02-11
forum: General Help
---

### Post by GrishinUS on 2008-02-11
Hello everyone!
I've got system with two hard disks :
-WinXP on primary master HDD;
-Ubuntu 7.10 on primary slave HDD;
and my system has only one IDE connector.
First, I had got the primary master CDRom and the primary slave HDD in order to install Ubuntu. After system was installed I checked it (everything was OK) and removed primary slave HDD with Ubuntu in order to install WinXP; After WinXP was installed I removed the CDRom and connected WinXp drive to primary master.
Ubuntu boots OK, but I couldn't boot WinXP. I've tried to add to menu.lst :
###########
title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1
###########
and
###########
title Windows XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
###########
and
 ###########
title Windows XP
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1
###########
but it doesn't boot. Why?

---

### Post by SpaceTeddy on 2008-02-11
googled the error and stumpled upon this... hope it helps 
[http://ubuntuforums.org/showthread.php?t=282545]("http://ubuntuforums.org/showthread.php?t=282545")

sometimes, google is your friend.....

---

### Post by GrishinUS on 2008-02-11
Thanks a lot. The problem was solved.

---

