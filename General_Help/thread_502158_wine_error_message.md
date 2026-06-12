---
title: "wine error message"
date: 2007-07-16
forum: General Help
---

### Post by zach12 on 2007-07-16
hi i'm trying to run some app in wine(they all work i looked on winehq.org)
here is the error message
> zach@zach-laptop:~$ wine itunes.exe
/home/zach/.wine/system.reg is not a valid registry file
/home/zach/.wine/userdef.reg is not a valid registry file
/home/zach/.wine/user.reg is not a valid registry file
wine: could not load L"c:\\windows\\system32\\itunes.exe": Module not found
 thanks

---

### Post by Gruelius on 2007-07-16
simple problem. its looking for itunes.exe in that directory.

Try

wine ./itunes.exe
or wine ~/itunes.exe


If not go with amarok, FANTASTIC! app

---

### Post by zach12 on 2007-07-16
ok i got a new error message 
> zach@zach-laptop:~$ wine ~/itunes.exe
wine: cannot find '/home/zach/itunes.exe
thanks
PS i'm just going to use itunes store and inport the the tunes to Songbird

---

