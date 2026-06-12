---
title: "Need help with reinstalling mysqladmiin"
date: 2008-05-23
forum: General Help
---

### Post by habuchas on 2008-05-23
I installed LAMP and I everything is working.  I thought I installed phpmyadmin correctly but couldn't get to it. I tried to do the apt-get uninstall and that didn't work.  So I did a find for all the files/directories with phpmy* and proceeded to rm  -Rf to whole lot.  I got rid of them all.  
However when I attempt to reinstall phpmyadmin with 'sudo apt-get install phpmyadmin' I get the message that "phpmyadmin is already the latest version 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."
phpmyadmin is nowhere to be found.  Where is the information that it is already installed that is preventing me from reinstalling it?  Any assistance would be appreciated.
habuchas

---

### Post by Barriehie on 2008-05-23
> **habuchas said:**
> I installed LAMP and I everything is working.  I thought I installed phpmyadmin correctly but couldn't get to it. I tried to do the apt-get uninstall and that didn't work.  So I did a find for all the files/directories with phpmy* and proceeded to rm  -Rf to whole lot.  I got rid of them all.  
However when I attempt to reinstall phpmyadmin with 'sudo apt-get install phpmyadmin' I get the message that "phpmyadmin is already the latest version 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."
phpmyadmin is nowhere to be found.  Where is the information that it is already installed that is preventing me from reinstalling it?  Any assistance would be appreciated.
habuchas
Try installing it with the --reinstall option.

Barrie

---

### Post by habuchas on 2008-05-24
Thanks, you put me on the right track.  From your pic I would guess you are stationed at Nellis. If so, congrat to you and all like you.  Have a great Memorial week end.
chas........

---

### Post by Barriehie on 2008-05-24
> **habuchas said:**
> Thanks, you put me on the right track.  From your pic I would guess you are stationed at Nellis. If so, congrat to you and all like you.  Have a great Memorial week end.
chas........

Anytime chas!
Barrie

---

