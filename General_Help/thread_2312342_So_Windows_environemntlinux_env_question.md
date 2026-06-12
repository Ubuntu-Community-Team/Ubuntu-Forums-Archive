---
title: "So Windows environemnt/linux env question"
date: 2016-02-03
forum: General Help
---

### Post by silverbullet007 on 2016-02-03
So having used Windows for 2 decades I know where to look for files when I'm trying to troubleshoot application issues.  Like I know to look in the Run and RunOnce keys in the registry for misbehaving TSRs and startup at logon apps. I know there are many, many folders in C:\Windows that I never need to touch, like ever.  I know that 95% of the files required for an app are to be found under Program Files. Is there a chart, diagram, schematic or a plain list somewhere that correlates things like this between OS's?

---

### Post by Vladlenin5000 on 2016-02-03
No, not really. And no needed anyway.
There's no registry nor user editable system files. The less you mess with those the better, i.e., stay in your userspace. Do NOT try to 'import' your Windows "power" user "tips&tricks" to any Linux environment because nothing that you currently know will work and most likely will just makes thing worse. Sooner than later you'll learn that you don't need to worry about the many things you worried about in the other OS.
If you have any issue please open a thread for each one and we'll try to help you out.

---

### Post by Habitual on 2016-02-03
```
env
``` works in Windows cmd and bash

[gconf-settings ]("https://projects.gnome.org/gconf/")# see also [https://help.ubuntu.com/community/GConfEditor](https://help.ubuntu.com/community/GConfEditor) # closer to a "registry" so use Caution.
and 
~/.config/autostart

for starters.
I don't use Ubu, but others may have something I don't know about, or forgot.


Hope that gets you started!

---

### Post by yancek on 2016-02-03
Try the link below.

[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

If that doesn't do the job for you, enter the following in your web browser search engine:

> understanding the linux filesystem structure

which will give you countless more links.

---

### Post by silverbullet007 on 2016-02-04
> **yancek said:**
> Try the link below.

[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

If that doesn't do the job for you, enter the following in your web browser search engine:



which will give you countless more links.

This is exactly what I needed. Thanks

---

