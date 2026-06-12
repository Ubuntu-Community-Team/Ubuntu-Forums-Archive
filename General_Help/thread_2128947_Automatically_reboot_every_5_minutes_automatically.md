---
title: "Automatically reboot every 5 minutes automatically (required for laptop testing)"
date: 2013-03-24
forum: General Help
---

### Post by iDudetu on 2013-03-24
Hi Everyone,

I am currently testing a laptop which I believe to be faulty (if you interested in a description of the fault that I am seeing please have a look at [http://forums.techguy.org/windows-7/1093118-do-laptops-crash-when-they.html](http://forums.techguy.org/windows-7/1093118-do-laptops-crash-when-they.html)). Many readers of this post will be pleased to hear that I have given up on Windows 7. I now need to find a way to automatically reboot my laptop every five minutes (I have set my logon to "automatic" during the Ubuntu installation - so no password entry is required). 

Any help here will be greatly appreciated.

Kind Regards,

Davo

---

### Post by matt_symes on 2013-03-24
Hi

You could try using the shutdown command.

```
/sbin/shutdown -r +5
```

The -r above will reboot the system.

Add this to the file

```
/etc/rc.local
```

before the exit 0; command.

Kind regards

---

