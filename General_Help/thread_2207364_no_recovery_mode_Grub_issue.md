---
title: "no recovery mode? Grub issue"
date: 2014-02-23
forum: General Help
---

### Post by christon74 on 2014-02-23
Hello Ubunters O:)
I have just installed Ubuntu 12.04 LTS on my small hp compaq nc 4200. The only problem is that Grub does not seem to function correctly. I do not see the page with all the options (Memtest, recovery mode...)
I have tried the TIMEOUT thing, not to much avail.... 
Why is that? :confused:
Once again, thank you in advance for all help and trouble.
Have a nice Sunday.
Chris.

---

### Post by Bucky Ball on 2014-02-23
Edit /etc/default/grub, look for this line and make it look like this:
```

GRUB_TIMEOUT=10
```

Reboot. Sorry if that's what you already tried. ;)

---

### Post by christon74 on 2014-02-25
Well, if I press the shift key, then all options are displayed and I can access the recovery mode. So, thread solved.

---

