---
title: "CUPS: SystemGroup is missing from cupsd.conf"
date: 2021-05-13
forum: General Help
---

### Post by penguin-fach on 2021-05-13
Having problems getting permissions setup for printing from a networked laptop to a shared printer on another Linux PC. All are using 20.04 LTS. Looking like it is a problem with CUPS permissions.

I have always understood that users need to be added to the lpadmin group to be able to fully control printers. [https://wiki.ubuntu.com/Security/Privileges#Configure_printers]("https://wiki.ubuntu.com/Security/Privileges"), says that the CUPS config file , /etc/cups/cupsd.conf, should have a  SystemGroup entry assigning print permissions to the lpadmin group.  However I have looked at this file on my laptop and the desktop PC (with the shared printer) and there is no SystemGroup entry anywhere in the cupsd.conf file. Even more confusingly [https://www.cups.org/doc/man-cupsd.conf.html](https://www.cups.org/doc/man-cupsd.conf.html) doesn't make any mention of SystemGroup.

I think this may be why I am getting a 'permission denied' error when  printing from the laptop.Can anyone shed any light on this or tell me the correct procedure to add the SystemGroup to cupsd.conf?

---

### Post by deadflowr on 2021-05-13
The SystemGroup are represented by the @SYSTEM entries as per the rules defined in the cups-files.conf file.

Look in cups-files.conf.
As it should have an entry which reads as:
> # Administrator user group, used to match @SYSTEM in cupsd.conf policy rules...
# This cannot contain the Group value for security reasons...
SystemGroup lpadmin 


---

