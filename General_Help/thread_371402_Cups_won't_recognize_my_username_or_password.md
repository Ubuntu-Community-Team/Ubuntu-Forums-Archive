---
title: "Cups won't recognize my username or password?"
date: 2007-02-26
forum: General Help
---

### Post by ngrundy on 2007-02-26
I have been trying to install my hp f335 printer for a while now. I finally got the ppd file and tried to install it in the cups website. When I add the ppd file and press "add printer" a password and username prompt appears. When I enter both and press "OK"  they aren't recognized, The prompt window just reappears.... these are my root username and password , right?

I am pulling my hair out over this thing?

Help?

---

### Post by llamakc on 2007-02-26
No, not the "root" user, but your username.

---

### Post by Jim Darrough on 2007-03-11
I am running 6.06LTS (which is great) but am trying to use CUPs to set up my HL-2070N network printer. I cannot make any changes because it does not recognize my username and password (the same one I logged into Ubuntu with). In short, I am having the same problem.

Anyone have any ideas for me?

Thanks, Jim in Oregon

---

### Post by llamakc on 2007-03-11
Ahh yes. Dapper's printing issue with CUPS and the web interface.

Select “System”->”Administration”->”Users and Groups” from the main menu on your desktop.
Select “Show all users” and/or “Show all groups”.
Add the user “cupsys” to the group “shadow” in the “groups” tab.
 Restart cupsys by issuing the command:
$sudo /etc/init.d/cupsys restart



Also, this works for me so CUPS just SEES my network printers.



```
sudo ln -s  ../backend-available/snmp /usr/lib/cups/backend/snmp
```

---

### Post by tommynz1975 on 2007-11-28
Thank you llamakc  A google got me to this thread..  For ages I have tried to setup my Apple 12/600 lasser printer. now I have got cups accepting my user name and password I hope to be lassering soon...

Can I please ask what 
the code

sudo ln -s  ../backend-available/snmp /usr/lib/cups/backend/snmp

actually does step as I am only learning... and would like to make a file of commands and what they exactly do..

---

