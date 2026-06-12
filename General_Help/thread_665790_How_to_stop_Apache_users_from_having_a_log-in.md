---
title: "How to stop Apache users from having a log-in"
date: 2008-01-12
forum: General Help
---

### Post by Duffy on 2008-01-12
I am trying to manage Apache and ProFTPD with Webmin and Virtualmin on Kubuntu. When I set-up a virtual name website, Virtualmin creates an administrator which is all well and good. But it also creates a log-in for the user so that when the system restarts, I have this long list of names. Also happens when any other user is created. Is there any settings that prevent a user from being listed on the log-in screen when the system first starts?

---

### Post by dcstar on 2008-01-13
> **Duffy said:**
> I am trying to manage Apache and ProFTPD with Webmin and Virtualmin on Kubuntu. When I set-up a virtual name website, Virtualmin creates an administrator which is all well and good. But it also creates a log-in for the user so that when the system restarts, I have this long list of names. Also happens when any other user is created. Is there any settings that prevent a user from being listed on the log-in screen when the system first starts?

System Settings-Advanced-Login Manager-Administrator Mode-Users uncheck "Show list", you can also alter the "Convenience" settings if you like.

---

### Post by Duffy on 2008-01-13
David,

Thanks - I did not know that was there.

Duffy

---

