---
title: "Stop asking me for a password when wakeing up from sleep"
date: 2016-03-12
forum: General Help
---

### Post by Kusho on 2016-03-12
How do I remove the need for Ubuntu to ask me for a password everytime it wakes up from sleep.  The only posts I found about this were from 11.04 and don't apply to 15.10.  I did find [http://askubuntu.com/questions/639014/another-password-prompt-when-waking-from-suspend](http://askubuntu.com/questions/639014/another-password-prompt-when-waking-from-suspend) but tried this fix sudo apt-get remove gnome-screensaver but it didn't fix the problem.

Thanks.

Tom

---

### Post by ajgreeny on 2016-03-12
This will be either in the power-management or perhaps the light-locker, (ie Brightness & Lock in unity), both found in system settings.

---

### Post by papibe on 2016-03-12
As ajgreeny commented it, open 'Brightness & Lock', and uncheck 'Requires my password when waking up from suspended'.

Let us know how it goes.
Regards.

---

### Post by Kusho on 2016-03-12
This fixed it when I also clicked Lock Off, also under Brightness & Lock.  Thanks for the tip.

---

### Post by ajgreeny on 2016-03-13
PLease mark this as SOLVED from the Thread Tools menu at the top

---

