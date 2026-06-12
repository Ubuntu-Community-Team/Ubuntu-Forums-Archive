---
title: "Error when starting KDE session"
date: 2007-06-01
forum: General Help
---

### Post by ghandi69_ on 2007-06-01
Hey guys.. I am getting this error when I start up KDE after having log outed or having the computer turned off.... The attached screenshot is what I'm looking at.

I've tried to add the section it describes into my xorg.conf file.. but it is still giving me the same error.

Once getting rid of that error... everything seems to work fine.. except I believe my panel has been cleared of its contents... all that remains is one transparent panel that you wouldn't even know was there....

---

### Post by tronica on 2007-06-01
So did add that section to your xorg.conf? The composite will not work if you have an ATI if i remember correctly. post your xorg.conf

---

### Post by ghandi69_ on 2007-06-01
Here it is....

---

### Post by merlinus on 2007-06-01
You might try using vesa instead of nvidia, and then can change it by installing the drivers when the os is booted.

-merlin

---

