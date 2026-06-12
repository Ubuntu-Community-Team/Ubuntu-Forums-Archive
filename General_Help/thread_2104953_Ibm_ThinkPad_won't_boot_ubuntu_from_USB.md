---
title: "Ibm ThinkPad won't boot ubuntu from USB"
date: 2013-01-14
forum: General Help
---

### Post by Not install on 2013-01-14
hi everyone I managed to create a persistant USB with the help of a forum user here I will search for his name and let you know thanks but now problem

Ibm ThinkPad refuses to recongzine Ubuntu  boot up USB  I uncheck in explorer and I here will then files so I now  it wars creatred properly

anyone had similar problems with ibm ThinkPad and booting ubuntu USB?

is this a common fault what can be done to fix this I even tried plop boot and same message the Lenovo reports no device attached when there is?

please please help or I can save any settings and need to use the persistent USB for saving my settings

Thankful for reading

---

### Post by steeldriver on 2013-01-14
What model of Thinkpad?

Some very old ones might not be able to boot from USB at all - OTOH some (like my X30) will boot from USB but it is rather confusingly listed in the BIOS under 'Hard drives' rather than 'Removable devices'

---

### Post by tgalati4 on 2013-01-14
So it was working OK, and now it is not working?

Put it in another linux machine, open a terminal, and post the following:

```
dmesg | tail -50
```

Back up any important user data to another flash drive, in case this one is faulty.

Does the USB port still work?  Can you put in a clean USB flash drive and add files to it?

---

### Post by Not install on 2013-01-15
Thnakyou its now working  USB was not created properly

Many thanks all

---

### Post by mörgæs on 2013-01-15
Good, please mark the thread 'solved'.

---

