---
title: "Keyboard Indicator Rename"
date: 2007-01-26
forum: General Help
---

### Post by Yumi on 2007-01-26
I use different Keyboard layouts. The Keyboard Indicator says eg. USA, Deu or Tur. How can I rename this 3 letter layout name?

Michael

---

### Post by Yumi on 2007-03-02
I finally found the solution. Edit the file /etc/X11/xkb/rules/xorg.xml . Around line 3164 (in my standard installation) replace all ocurances of USA with Eng. Voila, the keyboard indicator switches from Eng to Deu to Chi, the languages I use. No more USA!

Michael

---

### Post by dr_d12 on 2007-03-10
I think it's sufficient to rename USA to ENG in the line 
       <shortDescription>USA</shortDescription>

For example, I renamed GBr to ESP in the line 
        <shortDescription>GBr</shortDescription> 

...so that the UK international keyboard layout that I use to type Spanish characters says ESP. 
Before these changes, mine said USA (US English) and USA* (US International with dead keys). Now it says ENG (US English) and ESP (United Kingdom International with dead keys).
-D

---

### Post by lxowle on 2007-10-10
Thanks for this - I was looking to do exactly the same thing and I found this thread. The advice above works for Gutsy.

---

