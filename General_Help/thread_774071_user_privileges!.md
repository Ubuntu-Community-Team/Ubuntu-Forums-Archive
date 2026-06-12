---
title: "user privileges!"
date: 2008-04-29
forum: General Help
---

### Post by amazoohwawa on 2008-04-29
i am trying to set up my laptop for use with and external display and i keep getting this message when i type displayconfig-gtk at the terminal: 

> VESA BIOS Extensions not detected.


i am the only user on this laptop and i did check the user privileges and i do have administrative privileges!!

anyone has any ideas?? please help!!

---

### Post by kerry_s on 2008-04-29
did you use sudo?

---

### Post by Nunu on 2008-04-29
> **amazoohwawa said:**
> i am trying to set up my laptop for use with and external display and i keep getting this message when i type displayconfig-gtk at the terminal: 



i am the only user on this laptop and i did check the user privileges and i do have administrative privileges!!

anyone has any ideas?? please help!!

sudo -s displayconfig-gtk

Should do the trick.

---

