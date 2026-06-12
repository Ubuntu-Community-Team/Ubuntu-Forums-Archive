---
title: "Keyboard stopped working"
date: 2008-01-22
forum: General Help
---

### Post by kaflex on 2008-01-22
I have a Microsoft natural multimedia keyboard. I'm running Ubuntu 7.10 alongside Windows XP. I installed Ubuntu 7.04 and updated it to 7.10. The keyboard worked fine until I restarted the computer. Now it only works until the I select Ubuntu and it loads just fine, but I can't type my user name to log in. 

Jeff

---

### Post by mali2297 on 2008-01-24
Boot in recovery mode, and then type (if you can)
```

dpkg-reconfigure xserver-xorg

```
That starts a wizard that allows you to configure your keyboard layout, among other things.

---

### Post by kaflex on 2008-01-26
> **mali2297 said:**
> Boot in recovery mode, and then type (if you can)
```

dpkg-reconfigure xserver-xorg

```
That starts a wizard that allows you to configure your keyboard layout, among other things.

no can do, i boot into recover mode and the keyboard still don't work...this is starting to stress me out...I really prefer linux over windows:confused:

---

### Post by mali2297 on 2008-01-26
Can you work from the Live CD?

EDIT:
Stupid question perhaps, but anyhow...
Have you checked that the keyboard works in Windows?

---

### Post by kaflex on 2008-01-26
> **mali2297 said:**
> Can you work from the Live CD?

EDIT:
Stupid question perhaps, but anyhow...
Have you checked that the keyboard works in Windows?

I tried 7.04 live and 7.10 live and still don't work, keyboard works with windows:)

---

### Post by mali2297 on 2008-01-26
How did you install Ubuntu 7.04 in the first place? With the Alternate CD?

---

### Post by kaflex on 2008-01-26
Installed 7.04 from offical cd

---

### Post by mali2297 on 2008-01-26
If I understand you correctly, you once installed Ubuntu 7.04 from the Live CD without problems with the keyboard. Now, you cannot use the Live CD anymore, despite that it is the same CD and the same keyboard. That would suggest a hardware problem, but then again, the keyboard works when you use Windows on the same machine. :-?

I'm sorry, but I'm out of ideas.

---

### Post by kaflex on 2008-01-26
you got it right.  I even tried a different keyboard and that doesn't work either

---

### Post by kaflex on 2008-02-02
It started working again...I wish I knew what was going on

---

