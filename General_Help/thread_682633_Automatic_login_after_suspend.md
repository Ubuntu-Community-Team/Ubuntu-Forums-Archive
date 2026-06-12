---
title: "Automatic login after suspend"
date: 2008-01-30
forum: General Help
---

### Post by kwc01 on 2008-01-30
Hello,

I have my login options set to automatically login without prompting for a password upon startup of Ubuntu 7.10.  That works fine.  

But after suspending, I get the login screen when I recover from suspend.  Is there a way to bypass this as well?  The computer is intended for family use and I don't want everyone to have to enter a password each time they use it.

Thanks!
kwc01

---

### Post by nick_h on 2008-01-30
Try editing your acpi-support file using:
```
gksudo gedit /etc/default/acpi-support
```
and setting
```
LOCK_SCREEN=false
```

---

### Post by kwc01 on 2008-02-01
nick_h,

Thanks for the recommendation.

I tried it, and also commented out the line per the instructions in the acpi-support file, but neither was successful (even after rebooting).

Any additional thoughts?

kwc01

---

### Post by Tenken on 2008-02-01
Are you also using a screen saver with the "Lock screen when screen saver is active" option selected?

---

### Post by kwc01 on 2008-02-01
No, I don't have the "lock screen" box checked in the screensaver settings.  I am also using the standard screensaver themes (blank screen).

---

### Post by msjacoby on 2008-02-02
I have been having the same problem since updating to 7.10. Same as above - not using screensaver lock - tried setting SCREEN_LOCK to false as well as commenting out. Neither worked. It is a major pain to have to authenticate after suspend. Does anyone know the solution?

---

### Post by nick_h on 2008-02-04
The files to look at in debugging this problem would be:

/etc/acpi/sleep.sh which calls /usr/share/acpi-support/screenblank
and also /etc/acpi/resume.d/90-xscreensaver.sh which is called when resuming from suspend.

---

### Post by kwc01 on 2008-02-06
nick_h,

I tried commenting out all code in the 90-xscreensaver.sh script to no avail...

Thanks,
kwc01

---

