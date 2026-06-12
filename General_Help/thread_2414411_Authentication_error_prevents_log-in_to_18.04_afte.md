---
title: "Authentication error prevents log-in to 18.04 after upgrade from 16.04."
date: 2019-03-10
forum: General Help
---

### Post by Sleepy-zz-John on 2019-03-10
Online upgrade to 18.04 from 16.04 went OK until I tried to log-in to it.

Goes thru grub and 18.04 starts to load normally until it shows my username  ("Sleepy.jpg") [ATTACH=CONFIG]282737[/ATTACH]

Clicking on that immediately takes me very briefly to a 2nd page with authentication error ("AuthError.jpg") [ATTACH=CONFIG]282736[/ATTACH] without allowing any chance to enter a password before it disappears in less than 1 second. 

Then it sticks on a blank grey page which can only be shifted by a restart. 

Starting again and trying clicking on "Not listed" on that 1st username page once again takes me to the authentication error page.  This time it gives me longer to try different entries in its grey entry field (different usernames, passwords etc.) but they all take me to the same blank grey page that can only be shifted by a restart.  

Tried a few other things like Recovery mode from grub and found I can manage a successful terminal root login and go from ```
 root@TP-L520:~# 
```  to ```
 sleepy@TP-L520:~# 
``` 

Note: TP-L520 is my Lenovo ThinkPad 250's name.  However Recovery is in read-only mode and I don't really know what I'm doing there anyway.

I also have access via a LIVE DVD to some of my System files, for example bin, boot,  grub,  usr, var, etc,  but again don't really know what I'm doing or what to look for there.

Any thoughts, suggestions,  guidance much welcomed.

     +   John

---

