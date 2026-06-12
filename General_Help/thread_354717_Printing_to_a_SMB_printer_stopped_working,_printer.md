---
title: "Printing to a SMB printer stopped working, printers just keeps going into paused stat"
date: 2007-02-06
forum: General Help
---

### Post by styson on 2007-02-06
Greetings,

I have a Brother MFC-3420C printer that is hung off a windows 2003 server.  I have been happily printing to it for 2 months from my Laptop running Dapper Drake.  For some reason, I tried printing last night and the docs go into the print queue but the printer keeps showing paused.   I resume the printer but it goes paused again.   I've rebooted the laptop and server.. no change.  Any clues where to look for an error?  I've checked most of the log files and cannot see any smb related errors.  

The only thing new I've added to my laptop was installing Samba so I could share a folder with a Vmware session of XP.  Could that have borked things up?

Any help is appreciated

---

### Post by styson on 2007-02-06
I've narrowed the problem down to something not correct with my smb.conf file.  I put back the default one for ubuntu and printing started working again.   I'll dig into what is wrong with my file later on.

---

