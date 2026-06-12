---
title: "Print File Held for Authentication"
date: 2016-04-19
forum: General Help
---

### Post by mcman56 on 2016-04-19
I had been printing form Ubuntu through a wireless connection to a Windows Vista system with hardwired printer.  The printer is shared.  The Ubuntu system can access the internet thorough the wireless connection but it will no longer print.  I get a warning showing "Print File Held for Authentication".  The window with that warning has functions to authenticate and to release.  It will ask for a password but then nothing happens and it returns to the same screen.

---

### Post by mcman56 on 2016-04-24
I have lost the ability to print from my Ubuntu laptop through the wireless network to a printer attached to a Vista machine.  The job-printer-state-status says  NT_STATUS_ACCESS_DENIED.  The job-state-reason states cups-held-for-authentication.  If I click for printer status I see the same authentication statement.  I can right click to authenticate and enter the password it shows processing but then goes back to the authentication fail statement. I tried loading GADMIN-SAMBA and under users I see missing password.  When I add the password it will update but then goes back to missing.  It seems like it no longer likes the password.  Are the any ideas on how to proceed?

---

### Post by cariboo on 2016-04-24
Please don't create multiple threads on the same subject. I have merged your two threads.

It would have been a better idea to just bump the original thread.

---

### Post by mcman56 on 2016-04-25
Sorry, I thought I may have been in the wrong sector.  I unloaded and reloaded Samba and Cups but now have a different issue. Some screen prints are attached.

from printer properties- idle - File "/usr/lib/cups/backend/smb" not available: No such file or directory  - a file of that name is there but I can not open it with gedit

from print file - stopped - printer configuration error


[ATTACH=CONFIG]268632[/ATTACH][ATTACH=CONFIG]268631[/ATTACH][ATTACH=CONFIG]268634[/ATTACH]

---

