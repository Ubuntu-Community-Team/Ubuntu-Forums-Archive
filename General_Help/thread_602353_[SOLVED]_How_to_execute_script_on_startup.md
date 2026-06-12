---
title: "[SOLVED] How to execute script on startup?"
date: 2007-11-04
forum: General Help
---

### Post by MichaelSwengel on 2007-11-04
Apparently there is a bug in Feisty and Gutsy that can cause extra wear and tear on laptop hard drives, as explained [here.]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear")

The code to disable power management is "sudo hdparm -B 255 /dev/sda"

My question is this: Is there a way I can have this script executed every time I log on, instead of having to do it manually via Terminal? 

I'm running Gutsy on a Macbook Pro, so I don't know if this problem even applies, but I'd rather be safe than sorry.

---

### Post by Steve1961 on 2007-11-04
You could try putting it in /etc/rc.local (but without the 'sudo').  Make sure that rc.local is executable by doing sudo +x /etc/rc.local

---

### Post by Rinzwind on 2007-11-04
You only need to do that hdparm-command once and not every time you boot
Secondly: if you did NOT change the parameter enable_laptop from FALSE to TRUE you do NOT have to do anything since that parameter needs to be TRUE.

---

### Post by Rinzwind on 2007-11-04
Here's a simple check:

```
# more /etc/default/acpi-support | grep ENABLE_LAPTOP
```

Should result in:

```
ENABLE_LAPTOP_MODE=false
```

---

