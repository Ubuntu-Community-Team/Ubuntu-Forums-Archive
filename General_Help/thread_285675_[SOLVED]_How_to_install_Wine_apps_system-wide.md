---
title: "[SOLVED] How to install Wine apps system-wide"
date: 2006-10-27
forum: General Help
---

### Post by siddartha on 2006-10-27
Hello,

I have some windows apps who work just fine with Wine. I would like to install them system wide so all the users can bennefit from them. How do I do that? So it will work just like on Windows - the app will install somewhere in /usr for example and it will be unmodifiable for anybody but the root. Than, the configurations should be per user in their home directories, maybe under ~/.wine

So far I can get them installed on a virtual C: drive in my home directory. Installing the app for each user would be plain stupid as it will involve upgrading by hand for each instance and it will take quite a lot of space.

Thank you,
Sidd

---

### Post by cronholio on 2006-10-27
Create a folder /wine and a group wine. Add all users that should be able to run the applications to the group. Move the installations you have from ~/wine to /wine. Then:

```
sudo chgrp wine /wine
sudo chmod g+rx /wine
```

Finally, create appropriate launchers in the applications menu.

---

### Post by siddartha on 2007-01-28
Thank you.

---

