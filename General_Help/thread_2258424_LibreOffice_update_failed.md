---
title: "LibreOffice update failed"
date: 2014-12-27
forum: General Help
---

### Post by Bill_McConnell on 2014-12-27
After getting routine updates and restarting the computer, I git the following message for all LibreOffice applications.

"The application cannot be started. 
Failed to updatefile:///home/bill/.config/libreoffice/4/user/extensions/bundled/lastsynchronized"

I tried using synaptic update, but hope to avoid removing and reinstalling.  Any suggestions?

---

### Post by Holger_Gehrke on 2014-12-27
The file is used as a  timestamp, it's modification time is compared to the time of the last update of extension or extension configuration. During start-up libreoffice checks the configuration of extensions and updates the modification time of this file if everything went well. On your system this failed for some reason. Check the permissions on the file and the directory it's in.

---

### Post by ajgreeny on 2014-12-27
Check what is in that file as well; on my system it is a plain text file containing just one character, the number 1

---

### Post by Bill_McConnell on 2014-12-27
Thanks to both of you.  When I opened the file in vi, it showed the digit 1, and at the bottom was a message I had never seen before: "incomplete last line".

So, I added a carriage return, which made a second line.  I deleted that, and things are working.

Love the quick, kowledgeable help on the forums.

---

