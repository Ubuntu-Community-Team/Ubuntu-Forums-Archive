---
title: "Keyboard problems"
date: 2014-12-04
forum: General Help
---

### Post by Bruv on 2014-12-04
I am in the UK and need a pound sign at times.
My keyboard has the @ and " keys reversed, and no sign for pounds sterling.
I have a UK Keyboard in Settings with Generic 104-key PC showing.
Any help available ?

---

### Post by Y^2om&amp;#7sgP on 2014-12-04
check /etc/default/locale

I found it's often set by default to US, just change to GB

---

### Post by Bruv on 2014-12-04
Check command not found.
But as I said the keyboard is set to UK already

---

### Post by Bruv on 2014-12-04
Panic over.
I thought I had tweeked everything several times with no result.
I visited settings again to check and everything was set to UK.
But it is all OK now, after a regular Update, perhaps that did it.

---

### Post by Bruv on 2014-12-04
I have found that going to All Settings scroll down to Keyboard, add a UK Keyboard delete the old one, then close All Settings, and everything is OK £ sign and @ and " are in the right place.
After rebooting the keyboard reverts to having no £ sign and the other signs are reversed as before on the keyboard. 

How do I fix the problem permanently ?

---

### Post by tea for one on 2014-12-04
> **Bruv said:**
> Panic over.
I thought I had tweeked everything several times with no result.
I visited settings again to check and everything was set to UK.
But it is all OK now, after a regular Update, perhaps that did it.

I have been using Ubuntu for more than six years and I have also suffered this keyboard variation on 14.04.

Intermittently, the keyboard layout defaults to US English layout when I boot the PC into Ubuntu after using an OS  (eg Openelec) on an external USB hard drive.

I do not have a US English keyboard setting on my Ubuntu system, I only have UK English as a system default.

It is impossible to report a bug because the fault is not obviously triggered by a certain action.

I have discovered that if you log out and log in again, the problem disappears (temporarily)..........

I suspect that it will re-appear next week.

---

### Post by Bruv on 2014-12-04
Dont take this the wrong way, but I am happy others are finding the same problem as I thought it was something I had done wrong or messed up.
I am sure it will be sorted out, it is only a minor irritation anyway.

---

### Post by Bruv on 2014-12-07
I may have cured the problem, or at least worked around it.
After login I go to settings, keyboard then add a UK keyboard and delete the old one, when shutting down make sure to tick 'Save session'
It has been working after several restarts.

---

