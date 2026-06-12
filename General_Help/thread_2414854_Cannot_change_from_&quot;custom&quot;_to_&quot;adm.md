---
title: "Cannot change from &quot;custom&quot; to &quot;admin&quot; in &quot;users settings. &quot;"
date: 2019-03-16
forum: General Help
---

### Post by Nylo on 2019-03-16
I cannot change my account type from "custom" to "admin" in "users settings?"  When I click "change" in "Account type: custom" nothing happens. Its been like this since I installed 18.04 LTS.

Thanks, 
Nylo

Lubuntu 18.04 LTS

---

### Post by again? on 2019-03-16
Do you have an authentication agent running?
Lubuntu uses lxpolkit and you should see it in task manager or check running processes.
```
ps aux | grep [l]xpolkit
```

---

### Post by Nylo on 2019-03-16
That did it!  Installed lxpolkit and Im good to go.

Thank you so much,
Nylo

---

