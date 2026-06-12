---
title: "new adm group"
date: 2018-04-12
forum: General Help
---

### Post by sniper8752 on 2018-04-12
In going through my /var/log, I notice that some of the files are owned by the group, "adm".  Is this something that should be concerning?

---

### Post by steeldriver on 2018-04-12
No, that sounds completely normal - see [What is the "adm" group?](https://ubuntuforums.org/showthread.php?t=1318346)

---

### Post by Impavidus on 2018-04-12
That's normal. It means that users belonging to the adm group can read those log files, but ordinary users can't.

---

