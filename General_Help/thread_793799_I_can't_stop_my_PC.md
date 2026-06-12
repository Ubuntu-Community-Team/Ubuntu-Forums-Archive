---
title: "I can't stop my PC"
date: 2008-05-14
forum: General Help
---

### Post by EvilAngel on 2008-05-14
Hi all,

I have a fresh Kubuntu 8.04 install on an AMD64 PC.

When i want to switch off my PC, i am clicking in the KDE window to switch off.
The session is closed, the PC is shortly switching in console mode, the screen is getting black, but the electricity keeps on.

I have to manually use the power button to switch off the PC.

However, if i am typing *sudo halt* in a console, then the PC is switching off completely.

Any ideas ?

Thanks

---

### Post by mandrill on 2008-05-14
> **EvilAngel said:**
> Hi all,

I have a fresh Kubuntu 8.04 install on an AMD64 PC.

When i want to switch off my PC, i am clicking in the KDE window to switch off.
The session is closed, the PC is shortly switching in console mode, the screen is getting black, but the electricity keeps on.

I have to manually use the power button to switch off the PC.

However, if i am typing *sudo halt* in a console, then the PC is switching off completely.

Any ideas ?

Thanks
Refresh your screen, if that doesn't help, re-start X control/alt>delete. you will have log in again. This may or may not solve the problem....

---

### Post by balagosa on 2008-05-14
hmmm....I use 
```
sudo shutdown -P now
```

even made a launcher for it

---

### Post by EvilAngel on 2008-05-14
> Refresh your screenHow do I refresh the screen ?
Thanks

---

### Post by mandrill on 2008-05-14
> **EvilAngel said:**
> How do I refresh the screen ?
Thanks

I believe KDE has it in its right-click dropdown menu. If not, my apologies.

---

### Post by EvilAngel on 2008-05-14
Ok, i found the solution on another Ubuntu forum.

To fix the problem, you have to add
*apm power_off=1*

to /etc/modules file.

Now it works perfectly :)

---

