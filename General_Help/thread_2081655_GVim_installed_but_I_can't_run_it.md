---
title: "GVim installed but I can't run it"
date: 2012-11-07
forum: General Help
---

### Post by tc101 on 2012-11-07
I installed the GVim editor but I can't run it from the applications menu on my 10.04 machine.  I installed it on my 12.04 machine and I can open it from an icon but when I type in GVim or Vim in the dashboard it doesn't come up.

---

### Post by 2F4U on 2012-11-07
> I installed the GVim editor but I can't run it from the applications menu on my 10.04 machine.

Is there an error message? What happens if you start it from a terminal? At least then you should see errors, if there are any.

---

### Post by tc101 on 2012-11-07
I ran it from the terminal and it came up fine.  It just doesn't show up anywhere on the applications menu.

---

### Post by netopalis45 on 2012-11-07
If you can run it from the terminal all you have to do is go to the "Main Menu" item in the "System" and "Prefrences" sub menu (I think) dropdown list in your top panel and create a new launcher.  Select which menu you would like it in and hit the button labeled "New  Item" and then copy and paste this line into the command field 
```
gvim -f %F
```

---

