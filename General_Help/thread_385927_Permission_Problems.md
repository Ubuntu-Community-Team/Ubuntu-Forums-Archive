---
title: "Permission Problems"
date: 2007-03-16
forum: General Help
---

### Post by Moe70 on 2007-03-16
everyuthing i try to do an error message comes up saying i dont have permission. when right click my system files drive and click properties...permission and tick give 'write' and 'excute' permission it says i dont have permission to change that

what can i do

---

### Post by mcduck on 2007-03-16
That's normal, you are not supposed to have permissions to anything outside your home directory. Read these for more info: 
[http://www.psychocats.net/ubuntu/permissions]("http://www.psychocats.net/ubuntu/permissions")
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Anyway, if you need to have full access to something outside your home, press Alt-F2 and run 'gksudo nautilus' to open file manager as root user. But be careful with that, as it allows you to completely trash your system..

---

### Post by Moe70 on 2007-03-16
thanks :)

---

