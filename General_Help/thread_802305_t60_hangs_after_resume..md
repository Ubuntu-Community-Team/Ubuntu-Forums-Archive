---
title: "t60 hangs after resume."
date: 2008-05-21
forum: General Help
---

### Post by period3 on 2008-05-21
I have a thinkpad T60, 2GHz Core 1 Duo (T2500), 2 GB of memory, one SATA drive, and one PATA drive (in the ultrabay), ATI X1300

I haven't been able to suspend or hibernate for about a year and a half (since Dapper).

After every release, the symptoms change, but it still doesn't work.  

Right now it will suspend properly, but resume is slow.  Once it does resume, I can use my computer normally for about 30 seconds.  After that, whenever I launch an application (say, gnome-terminal), the window is drawn blank.

Any thoughts on what could be wrong, or how to go about debugging this problem?

---

### Post by tormod on 2008-05-22
Could be the graphic driver. Try the "vesa" driver first. And try disabling DRI if you're using the -ati driver. Other than that, check with other T60 owners or look in the bug database if others have the same issue.

---

### Post by strabes on 2008-05-22
I assume you are using fglrx? If so, good. ATI finally added support for suspend & hibernate in hardy. Please open the file /etc/default/acpi-support:

```
gksudo gedit /etc/default/acpi-support
```

Change this line:
SAVE_VBE_STATE=true
to
SAVE_VBE_STATE=false

Also change this line:
POST_VIDEO=true
to
POST_VIDEO=false

Reboot and let us know if this helps.

---

### Post by sedated on 2011-06-22
Thanks strabes ,

I don't have an t60 but have ATI graphic card, changing acpi-support worked for me.

---

