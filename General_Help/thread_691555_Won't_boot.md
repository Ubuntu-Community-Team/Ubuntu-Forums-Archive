---
title: "Won't boot"
date: 2008-02-08
forum: General Help
---

### Post by jamsh on 2008-02-08
I downloaded from Sourceforge . When I rebooted as requested and was offered the option XP or UBUNTU, I highlighted UBUNTU , pressed 'enter'and got the following message   -   ERROR 17: file not found.
How can I fix this?

---

### Post by ago on 2008-02-09
Uninstall and try version 8.04 here (requires new iso):

[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

---

### Post by jamsh on 2008-02-09
Thanks for the reply.  I have uninstalled and downloaded from that link and now when I select Ubuntu at startup I get this message -
 File missing or corrupt
<Windows root>\system32\hal.dll
Please re-install the above file.

What can I do now?

---

### Post by ago on 2008-02-10
Uninstall, make sure you do not have any wubildr* or grldr* or menu.lst files in C:/ (or in the other drives). Then reinstall

---

### Post by jimbom on 2008-02-11
hall.dll is missing?? well u wont be able to boot windows either. I know of quite a few people who face this issue with wubi - it going and messing with the windows install. You now have to format and resinitall windows, download ubuntu and DO NOT use wubi. 

the wubi guys are doing quite a disservice by providing such a POS version of wubi.

---

