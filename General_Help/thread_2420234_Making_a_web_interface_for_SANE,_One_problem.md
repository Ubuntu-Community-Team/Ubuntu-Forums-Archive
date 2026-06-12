---
title: "Making a web interface for SANE, One problem"
date: 2019-06-01
forum: General Help
---

### Post by markosjal on 2019-06-01
I am making a web interface for SANE and have encountered one problem

Webserver can scan with php code using 

scanimage >file

however, 
scanimage -T -d "scannername"

does not work when run from apache / PHP

I suspect that there is a SANE group that users must get added to but typing groups does not show any such group , but it does not show a group for www-data either

so I ran
sudo usermod -a -G saned www-data

and still can not run the

scanimage -T -d "scannername" 

command from the web server. Also tested the resulting command from terminal and it works. I also replaced the command with ls -l and that works. 

Anyone have a clue?

---

### Post by Holger_Gehrke on 2019-06-01
The 'groups' command only lists the groups the user executing it is a member of, not all groups. A list of all groups can be found in /etc/group. And unless I'm very mistaken, the group you need to be member of to use sane is named 'scanner'.

Holger

---

### Post by markosjal on 2019-06-01
Thanks for the tip There is a group scanner. www-data is now a member of both saned and scanner groups but stilll no luck.

Strange part is I can use scanimage to scan from www-data just not get scanner info.

Just made it part of adm group too no luck still

---

