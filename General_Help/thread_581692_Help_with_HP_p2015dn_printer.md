---
title: "Help with HP p2015dn printer"
date: 2007-10-19
forum: General Help
---

### Post by D_dog on 2007-10-19
This seems to be the strangest problem I can not solve. I have a networked HP 2015dn printer. The software seems to be installed correctly. When I send it a print job it receives the job but the amber light flashes. It will not print the job until I push the button by the amber light. After pushing it the job prints flawlessly, even a duplex print. This happens with all three of my computers running Ubuntu. I have searched here and the HP sight with no answers to my problem. Does any one have an idea how to make it work correctly?

As a side note when the others in the house print to it using windoze it works fine.

---

### Post by linuxwizard on 2007-10-19
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by squeakyfrommage on 2008-04-22
I'm having the same issue, and I don't see a solution on the network printing page.  Did you ever get it solved?  I'd rather not have to hit a button on the printer everytime anyone wants to print.

---

### Post by squeakyfrommage on 2008-04-29
I downloaded a new ppd from here: [http://openprinting.org/foomatic-db/db/source/PPD/HP/](http://openprinting.org/foomatic-db/db/source/PPD/HP/)   file [http://openprinting.org/foomatic-db/db/source/PPD/HP/HP_LaserJet_P2015.ppd](http://openprinting.org/foomatic-db/db/source/PPD/HP/HP_LaserJet_P2015.ppd) . Then moved the ppd to the appropriate folder, and via the web interface (localhost:631) I modified the printer to use that instead of the other p2015  ppd.  Now there is no need to press the button. I found the solution here: [https://answers.launchpad.net/ubuntu/+question/22565](https://answers.launchpad.net/ubuntu/+question/22565)

---

