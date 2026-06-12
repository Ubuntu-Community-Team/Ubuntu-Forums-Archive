---
title: "single boot no menu choices"
date: 2007-06-25
forum: General Help
---

### Post by johnn1949 on 2007-06-25
I have a single boot Dapper.  When it boots up I don't see a menu that gives me a choice to boot into recovery mode.  The default boot is 0. and the time out is 3.  But I never see the menu that I see in a dual boot.  How do I boot to the recovery mode?

Thanks.johnn1949

---

### Post by yabbadabbadont on 2007-06-25
Hit the escape key before grub times out and starts booting.

---

### Post by johnn1949 on 2007-06-26
Thanks,  I'll try it.

---

### Post by louieb on 2007-06-26
You might be interested in two options found in /boot/grub/menu.lst. hiddenmenu and timeout. They are self explanatory.  By example heres mine.
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

---

