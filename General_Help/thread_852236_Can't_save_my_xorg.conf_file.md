---
title: "Can't save my xorg.conf file"
date: 2008-07-07
forum: General Help
---

### Post by Breetai on 2008-07-07
Not sure where this question really belongs.  But I'm running dual monitors and every time I reboot I have to reset my Nvidia X Server Settings.  By default my monitor's load in backwards of the way they should be.   No problem right?  I correct this in the Nvidia X Server settings hit apply the changes get made for the current session then save and it's telling me it's unable to remove the old X config backup file and doesn't save.  I'm almost certain it's a permissions issue but I only made one account to avoid such issues.  Shouldn't it be prompting me or something?  How do I make it save?

Thanks lots
Russ

---

### Post by damis648 on 2008-07-07
xorg.conf is owned by root. You must run nvidia-settings as root. In terminal, run
```
sudo nvidia-settings
```
and retry.

---

### Post by Breetai on 2008-07-07
Gotcha!  Thanks Bro!  That explains lots of other stuff.

---

### Post by damis648 on 2008-07-07
> **Breetai said:**
> Gotcha!  Thanks Bro!  That explains lots of other stuff.

You are welcome! Good luck!

---

