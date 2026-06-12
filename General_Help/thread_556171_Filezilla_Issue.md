---
title: "Filezilla Issue"
date: 2007-09-21
forum: General Help
---

### Post by sugan on 2007-09-21
hey,

Here i have new issue with my filezilla, when ever i try to connect to mysite.com using filezilla i get some error message saying "unable to connect" but i was able to connect to the same site using gftp(linux OS) what is the issue. i have also reinstalled the filezilla, but it dosnt work..

Regards,
Sugan

---

### Post by prince_niceguy on 2007-09-21
can you run filezilla from the terminal and revert back with the error in the console... that will help...

i am sure you would have checked this but are you connecting using secured shell in gftp and normal in filezilla?

---

### Post by liviubero on 2007-09-25
Perhaps I just had the same problem: 

> Status:    Connection established, waiting for welcome message...
Response:    220-FTP server ready.
Status:    Invalid character sequence received, disabling UTF-8. Select UTF-8 option in site manager to force UTF-8.
Response:    
Error:    Connection timed out
Error:    Could not connect to server
Status:    Waiting to retry...
I made filezilla working by doing: file->site manager->select the site and then, on the tab "Charset" enter ASCII

---

