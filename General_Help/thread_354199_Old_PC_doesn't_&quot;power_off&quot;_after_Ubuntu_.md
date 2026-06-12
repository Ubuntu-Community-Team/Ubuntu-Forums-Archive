---
title: "Old PC doesn't &quot;power off&quot; after Ubuntu shutdown"
date: 2007-02-05
forum: General Help
---

### Post by bash on 2007-02-05
Problems actually quite easy. My main Comp broke so I switched to this old P3 I found in ma celler. Its bout 7 years old. One of the really early machines to implement the new ATX standard for mainboards. Now the problem is that when I shut down the machine, it doesn actually switch the power off. It stays on after Ubuntu is fully shutdown.

In Windows this was easy to stop. You just had to activate the "Advanced APM" option in the Settings. Now I already questioned the mostly all-knowing (including your private stuff xD) Google. But didn't find anything useable. Anyone got an idea how to fix this.

---

### Post by Ramses de Norre on 2007-02-05
Install sysv-rc-conf: ```
sudo aptitude install sysv-rc-conf
``` and check for the apm services being enabled (an X) on runlevel 2 or S.

If that's already so: what happens when you use the following commands: (both should shutdown the machine) ```
sudo shutdown -h now
sudo init 0
```

---

### Post by Roaring Silence on 2008-02-10
How do you check that the APM services have been enabled?
Thanks,
Roaring Silence

---

