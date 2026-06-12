---
title: "ClamTK"
date: 2013-03-17
forum: General Help
---

### Post by christon74 on 2013-03-17
Hello every Ubunters :)
ClamTK (antivirus) really sucks. Virus definition outdated, GUI outdated and the 'Help' thing is not of much use either. How the hell do you update GUI and your virus definitions? Will somebody ever come up with an antivirus which automatically updates? 
I fear I can only whistle for it.....

---

### Post by varunendra on 2013-03-17
*Thread moved to **General Help**.*

> **christon74 said:**
> How the hell do you update GUI and your virus definitions?
GUI normally gets updated with regular updates, and for updating database -
```
freshclam -v
```

By the way, it does get updated with regular updates, not as frequently as windows AVs though, since we don't have that much urgency. When we have, we can use the above command.

---

### Post by deadflowr on 2013-03-17
Your virus definitions should be updated with every boot.
Freshclam starts when the system starts.
To update the GUI and the engine, go here:

[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

Click on the Debian/Ubuntu link.

If on Normal Ubuntu, double click to open the software center, and it'll offer an upgrade.
When upgraded all setting should be up-to-date.

Why the repos hold such an old version, I don't know.

---

### Post by christon74 on 2013-03-17
On second thoughts... I am giving up looking for an antivirus software.

---

### Post by deadflowr on 2013-03-17
> **christon74 said:**
> On second thoughts... I am giving up looking for an antivirus software.

Probably for the best, as I find the AV for linux to be pretty generic compared to Windows versions.
Sometimes, I think worrying about a bunch of Windows viruses on my linux system seems trivial.
Looky here on adding extra security on your linux install:
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

that is, if extra security is what you are looking for.

---

### Post by christon74 on 2013-03-17
Ok, Have finally found a way to update/upgrade Clam TK.

---

### Post by christon74 on 2013-03-17
Solved _ solved_ solved _solved

---

### Post by varunendra on 2013-03-18
> **christon74 said:**
> Ok, Have finally found a way to update/upgrade Clam TK.

> **christon74 said:**
> Solved _ solved_ solved _solved

Then please consider sharing the method you found and marking the thread as [SOLVED] to help others.

Thanks!

---

