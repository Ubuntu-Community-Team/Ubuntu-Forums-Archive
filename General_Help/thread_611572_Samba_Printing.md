---
title: "Samba Printing"
date: 2007-11-13
forum: General Help
---

### Post by mahousaru on 2007-11-13
For as long as I can remember I've always had to add to the Printer section of my smb.conf:

use client driver = Yes

If I don't my XP boxes will display "Unable to access printer" against the Samba printer.  I'm guessing that this value allows a client to connect to the samba printer with it's own drivers.  

The thing is by default it isn't set on SuSE or Ubuntu.  

Am I doing things in the right way?  I asked on various SuSE forums in the past and I've had a look around on the samba main site but couldn't get an answer.

Cheers in advance

---

