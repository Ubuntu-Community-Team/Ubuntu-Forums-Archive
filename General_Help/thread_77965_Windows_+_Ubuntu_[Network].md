---
title: "Windows + Ubuntu [Network]"
date: 2005-10-17
forum: General Help
---

### Post by megabajt on 2005-10-17
I have 5 computers with windows (98 and XP home) connected LAN and one computer with Ubuntu 5.04. I would like to use printer (HP 3820) connected to Windows XP computer. How to configure Ubuntu to use this printer?

Your help will be most appreciate.

---

### Post by ghosthere on 2005-10-17
I have about the same setup. I set mine up this way.
I setup my PC printer to share, then on my 5.10,
SYSTEM->Administration->Printing
Printer Type: Network Printer Windows Printer (SMB)
Host *PC DNS Name* a pop up box to log on to PC
Then slected Printer (or I typed in the share name)
pressed forward
Seleted Manufacturer my case HP
Then Model mine was deskjet 5550
Then Apply
I hope this helps

---

### Post by megabajt on 2005-10-18
So, should I configure samba at first? Do you know if samba is installed during standard installation?

How to check it that samba is installed and working? I know that I need to modify samba configuration file. How to do it ?

---

### Post by chinaski on 2005-10-18
there are many topics on this subject, I think a "search" will give you a lot of answers

---

