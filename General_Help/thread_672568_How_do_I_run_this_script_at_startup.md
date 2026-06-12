---
title: "How do I run this script at startup???"
date: 2008-01-19
forum: General Help
---

### Post by mikeyandmary on 2008-01-19
I want to run a script at srartup that will start irexec. 

I put this script in /etc/init.d and symlinked it to /etc/rcS.d

When I start the computer and check using "ps -A" irexec is not listed.

Any assistance would be appreciated
Michael




#!/bin/bash
irexec -d /home/macy/.lircrc
exit 0

---

### Post by popch on 2008-01-19
Try ***.profile*** in your home directory

---

### Post by nick_h on 2008-01-19
Try putting the command in your /etc/rc.local file.

---

### Post by capink on 2008-01-19
> **mikeyandmary said:**
> I want to run a script at srartup that will start irexec. 

I put this script in /etc/init.d and symlinked it to /etc/rcS.d

When I start the computer and check using "ps -A" irexec is not listed.

Any assistance would be appreciated
Michael




#!/bin/bash
irexec -d /home/macy/.lircrc
exit 0

You have to make sure the symlink on /etc/rc2.d/ starts with S99. (the S must be upper case)

```
sudo ln -s /etc/init.d/irexec /etc/rc2.d/[COLOR="Red"]S99[/COLOR]irexec
```

---

