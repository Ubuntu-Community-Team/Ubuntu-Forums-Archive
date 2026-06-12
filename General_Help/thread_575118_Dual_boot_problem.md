---
title: "Dual boot problem"
date: 2007-10-13
forum: General Help
---

### Post by chris670 on 2007-10-13
ok, dont ask how, but my sister, overwrited ubuntu with xp, and then my dad formatted the drive..

so now, when i boot up it comes up with dual boot

Windows XP - D: - comes up with an error message 'cant find this blah blah..'
Windows XP - C: - works fine..

i was wondering what to do? just to get rid of the faulty XP.

thanks. :)

---

### Post by Pumalite on 2007-10-13
Sounds like a question for Micro&%$. Doesn't it?

---

### Post by prince_niceguy on 2007-10-13
Open up boot.ini in c: with notepad... you will have to enable display system files in the explorer to view it...

now delete the line which gives d:... or alternate is to us msconfig or configmsi from run command... and modify the entry under boot.init

the latter approach is preferred one as you might mess up the boot.ini and you will have to use the rescue cd to modify the details...

---

